# DailyCodingProblem478 (Go)

## 問題描述
Implement a file syncing algorithm for two computers over a low-bandwidth network. What if we know the files in the two computers are mostly the same?

## 解題思路

- 透過雜湊可以知道檔案是否一致
- 題目要求是low-bandwidth network，所以將一個檔案拆成一群固定的bytes

## 程式碼
```
import (
"crypto/sha256"
"fmt"
)

func main() {
	content := []string{
		"Go",
		"Python",
		"Ruby",
		"PHP",
	}
	merkleTree := BuildTree(len(content))
	merkleTree.put(content)
	merkleTree.calcRootHash()

	content2 := []string{
		"Go",
		"Python",
		"Ruby",
		"PHP2",
	}
	merkleTree2 := BuildTree(len(content2))
	merkleTree2.put(content2)
	merkleTree2.calcRootHash()
	differNode := checkDifferMerkleTreeNode(merkleTree, merkleTree2)
	if differNode != nil {
		merkleTree2 = mergeDifferNode(differNode, merkleTree2)
	}
	merkleTree2.calcRootHash()
	fmt.Println(merkleTree.getRootHash() == merkleTree2.getRootHash())
}


type Node struct {
	id  int
	Val [32]byte
}
type MerkleTree struct {
	height int
	Node   *[]Node
}

func (merkleTree *MerkleTree) put(strArray []string) {
	for i := 0; i < len(strArray); i++ {
		leafNode := (1 << (merkleTree.height - 1)) + i
		(*merkleTree.Node)[leafNode].Val = sha256.Sum256([]byte(strArray[i]))
	}
}

func (merkleTree *MerkleTree) getRootHash() [32]byte {
	return (*merkleTree.Node)[1].Val
}

func (merkleTree *MerkleTree) calcRootHash() {
	size := len(*merkleTree.Node)
	for i := size - 1; i > 1; i = i - 2 {
		nodes := *merkleTree.Node
		digest := sha256.Sum256(append(nodes[i-1].Val[:], nodes[i].Val[:]...))
		(*merkleTree.Node)[i/2].Val = digest
	}
}

func BuildTree(size int) *MerkleTree {
	treeHeight := calcMerkleTreeHeight(size)
	if treeHeight < 0 {
		return nil
	}
	nodes := make([]Node, 1<<treeHeight)
	for i := len(nodes) - 1; i > 0; i-- {
		nodes[i] = Node{
			id:  i,
			Val: [32]byte{},
		}
	}
	return &MerkleTree{
		height: treeHeight,
		Node:   &nodes,
	}
}

func calcMerkleTreeHeight(size int) int {
	treeHeight := 1
	for i := 1; i <= 21; i++ {
		treeSize := 1 << i
		if size < treeSize {
			treeHeight = i
			break
		}
	}
	return treeHeight
}
func checkDifferMerkleTreeNode(tree *MerkleTree, tree2 *MerkleTree) []Node {
	if tree.getRootHash() == tree2.getRootHash() {
		return nil
	}
	var differNode []Node
	for index, node := range *tree.Node {
		node2 := (*tree2.Node)[index]
		if node.Val != node2.Val {
			differNode = append(differNode, node)
		}
	}
	return differNode
}
func mergeDifferNode(differNode []Node, tree *MerkleTree) *MerkleTree {
	for _, differNode := range differNode {
		(*tree.Node)[differNode.id].Val = differNode.Val
	}
	return tree
}

```

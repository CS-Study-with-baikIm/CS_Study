# 다양한 Tree

# 이진 트리 (Binary Tree)

이진트리는 트리 중에서도 각 노드가 최대 2개의 자식 노드를 가질 때 이진트리 라고 한다.

- 자식 노드에는 왼쪽 자식 노드와 오른쪽 자식노드가 있으며 이 둘은 엄연히 다른 노드이다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbxIAsK%2FbtrVcNLShyB%2FR9bONjmLtaf7nLCbPeECzK%2Fimg.png)   

## 이진 트리 종류

-정 이진 트리(Full Binary Tree)
정 이진트리는 트리의 모든 노드가 0개 혹은 2개의 자식을 가지는 경우이다. 즉 자식을 하나만 가진 노드가 없어야 한다. 그래서 다음 그림의 트리는 정 이진트리가 된다.

 ![title](https://3.bp.blogspot.com/-3t0IXok7ETE/Vt8Td3jbbGI/AAAAAAACZOc/j7SnIqBom8I/s1600/Full_binary.pdf.jpg)   


- 포화 이진 트리(Perfect Binary Tree)

포화 이진 트리는 마지막 리프노드를 가진 레벨이 노드를 더 추가할 수 있는 공간없이 가득 차 있는 이진 트리를 말한다. 따라서 포화 이진 트리의 노드 개수는 항상 트리의 높이 h에 대해 2^h - 1 개가 된다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FFYcPN%2FbtrnUJaMImr%2Fek0Jp10H9aps0pESJN04C0%2Fimg.png)

- 완전 이진 트리(Complete Binary Tree)

완전 이진 트리는 모든 레벨이 왼쪽부터 채워져있는 트리를 의미한다.    

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fex8hJX%2FbtrnW2HdtSB%2FSZYkNoVzmReLK8pFpP3imK%2Fimg.png)   


## 이진 트리 순회

이진 트리는 트리와 트리에 포함된 서브 트리들의 루트 노드를 언제 방문하는지에 따라 세 가지 방법으로 트리의 전체 노드를 순회할 수 있다.

 
- 전위 순회

전위 순회는 다른 노드들을 방문 하기 이전에 루트노드를 먼저 방문하는 순회방식입니다. 루트 -> 왼쪽 -> 오른쪽 순으로 트리의 노드들을 방문한다고 생각하면 된다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FZszfH%2FbtrnTDhI2GF%2Faw6UsuTRpIuop2CP7RPlw0%2Fimg.png)   


이 트리를 전위 순회하면 A->B->D->E->C->F->G 의 순서대로 방문하게 된다. 보이듯이 어떤 노드의 서브트리를 순회할 때는 해당 노드의 왼쪽의 모든 서브트리가 완료되어야 오른쪽 서브트리를 순회하게 된다. 

 

- 중위 순회

중위 순회는 루트 노드를 중간에 방문하는 순회 방법이다. 따라서 왼쪽->루트->오른쪽의 순서대로 노드를 방문하게 된다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdhc6O1%2FbtrnXZKkQev%2FvLo3TEKSxFnJHvU6Qcl2eK%2Fimg.png)   

위 예시와 동일한 트리를 중위 순회하게 되면 D->B->E->A->F->C->G의 순서대로 노드를 방문한다.

 

- 후위 순회

후위 순회는 루트 노드를 가장 마지막으로 방문하는 순회 방법이다. 왼쪽 서브트리의 탐색이 항상 오른쪽보다 선행되기 때문에 왼쪽->오른쪽->루트의 순서대로 노드를 방문하게 된다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FS1Dad%2FbtrnR2hNkO3%2FPfucZnpGfk9arPaAhUbKm1%2Fimg.png)   


동일한 트리를 후위 순회하면 D->E->B->F->G->C->A의 순서대로 방문하게 된다. 서브트리를 구성하는 루트 노드는 자신의 왼쪽과 오른쪽 자식노드가 모두 방문 된 이후에 방문된다. 

## 이진 탐색 트리(Binary Search Tree, BST)

**이진 탐색 트리**는 이진 탐색이 가능한 트리이다. 따라서 이진 트리에서 두 가지 조건을 만족하는 트리를 이진 탐색 트리 라고 한다.

- 이진 트리 내의 데이터는 유일 해야하고, 노드 내의 데이터 는 반드시 존재해야한다.
- 이진 트리 내의 왼쪽 자식 노드는 항상 부모 노드보다 작아야하며, 오른쪽 자식 노드는 항상 부모 자식 노드보다 커야한다.

![title](https://blog.kakaocdn.net/dn/d3DKwH/btqSKNgOjSV/sl1TR7sucngo5vMi742yn0/img.gif)   

위에 과정을 거쳐 구현이 되는것이 이진 탐색 트리이다.

## Swift로 구현
```swift
import Foundation

class Node {
    var data: Int //데이터는 항상 존재해야 한다.
    var parent: Node?
    var left: Node?
    var right: Node?
    
    init(data: Int) {
        self.data = data
    }
    
    var isRoot: Bool {
        return parent == nil
    }
    
    var isLeaf: Bool {
        return left == nil && right == nil
    }
    
    var isFull: Bool {
        return left != nil && right != nil
    }
}

class BinarySearchTree {
    var root: Node?
    
    func insert(_ data: Int) {
        guard let root = root else {
            self.root = Node(data: data)
            return
        }

        var currentNode: Node = root
        while true {
            //BST의 값은 유일해야 한다.
            if currentNode.data == data {
                return
            }
         
            if currentNode.data > data {
                //삽입할 값이 현재 노드의 값보다 작으면 왼쪽 노드로 이동한다.
                guard let nextLeftNode = currentNode.left else {
                    //왼쪽 노드가 비어 있으면 새로운 노드를 생성, 삽입한다.
                    currentNode.left = Node.init(data: data)
                    currentNode.left?.parent = currentNode
                    return
                }
                
                currentNode = nextLeftNode
            } else {
                //삽입할 값이 현재 노드의 값보다 크면 오른쪽 노드로 이동한다.
                guard let nextRightNode = currentNode.right else {
                    //오른쪽 노드가 비어 있으면 새로운 노드를 생성, 삽입한다.
                    currentNode.right = Node.init(data: data)
                    currentNode.right?.parent = currentNode
                    return
                }
                
                currentNode = nextRightNode
            }
        }
    }
    
    func remove(_ data: Int) -> Bool {
        guard let targetNode = search(data) else { //탐색 실패
            return false
        }
        
        if targetNode.isRoot { //root 노드를 지우는 경우
            removeRoot(targetNode)
        } else if targetNode.isLeaf { //Leaf 노드인 경우
            removeLeaf(targetNode, data: data)
        } else {
            if targetNode.isFull { //자식 노드가 2개인 경우
                removeFullNode(targetNode, data: data)
            } else { //자식 노드가 1개인 경우
                removeSingleChildNode(targetNode, data: data)
            }
        }
        
        return true
    }
    
    private func removeRoot(_ node: Node) {
        if node.isLeaf {
            root = nil
        } else if node.isFull {
            var changeNode = node.right!
            while let nextNode = changeNode.left {
                changeNode = nextNode
            }
            
            changeNode.left = root?.left
            changeNode.right = root?.right
            root = changeNode
            
            changeNode.parent?.left = nil
        } else {
            if node.left != nil { //왼쪽 노드만 있는 경우
                node.left?.parent = nil
                root = node.left
            } else if node.right != nil { //오른쪽 노드만 있는 경우
                node.right?.parent = nil
                root = node.right
            }
        }
    }
    
    private func removeLeaf(_ node: Node, data: Int) {
        if node.parent?.left?.data == data { //왼쪽 노드일 경우
            node.parent?.left = nil
        } else { //오른쪽 노드일 경우
            node.parent?.right = nil
        }
        node.parent = nil
    }
    
    private func removeSingleChildNode(_ node: Node, data: Int) {
        guard let parent = node.parent else { return }
        
        if node.left != nil { //target의 왼쪽 노드가 존재하는 경우
            if parent.data > data {
                parent.left = node.left
            } else {
                parent.right = node.left
            }
            node.left?.parent = parent
        } else { //target의 오른쪽 노드가 존재하는 경우
            if parent.data > data {
                parent.left = node.right
            } else {
                parent.right = node.right
            }
            node.right?.parent = parent
        }
    }
    
    private func removeFullNode(_ node: Node, data: Int) {
        guard let parent = node.parent else { return }
        guard let rightNode = node.right else { return }
        
        var changeNode = rightNode
        while let nextNode = changeNode.left {
            changeNode.parent = changeNode
            changeNode = nextNode
        }
                
        if let changeChildNode = changeNode.right {
            //변경할 노드가 leaf가 아닌 경우 -> right 노드가 있는 경우
            changeNode.parent?.right = changeChildNode
            changeChildNode.parent = changeNode
        } else {
            changeNode.parent?.right = nil
        }
        
        if parent.data > changeNode.data {
            parent.left = changeNode
        } else {
            parent.right = changeNode
        }
        changeNode.parent = parent
        
        changeNode.left = node.left
        changeNode.right = node.right
    }
    
    func search(_ data: Int) -> Node? {
        var currentNode: Node? = root
        while let node = currentNode {
            //찾는 값이 있으면 break
            if node.data == data { break }
            
            //이진 탐색
            currentNode = (node.data > data) ? node.left : node.right
        }
        
        return currentNode
    }
}

extension BinarySearchTree {
    func drawDiagram() {
        print(diagram(for: self.root))
    }
    
    private func diagram(for node: Node?,
                         _ top: String = "",
                         _ root: String = "",
                         _ bottom: String = "") -> String {
        guard let node = node else {
            return root + "nil\n"
        }
        if node.left == nil && node.right == nil {
            return root + "\(node.data)\n"
        }
        return diagram(for: node.right, top + " ", top + "┌──", top + "│ ")
            + root + "\(node.data)\n"
            + diagram(for: node.left, bottom + "│ ", bottom + "└──", bottom + " ")
    }
}
```

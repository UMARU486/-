# 30 thoughts about tree data structure

This is a collection of exercises that have been collected in wangdao 408 exercises. 

The goal of this collection is to offer a quick reference for cpp freshmans like me.

If you find an error or think you've a better way to solve some of them, feel
free to open an issue at <https://github.com/UMARU486/->.

#### Design an algorithm to determine whether two binary trees are similar. Two binary trees T1 and T2 are considered similar if they are both empty, have only one root node, or if the left subtree of T1 is similar to the left subtree of T2 and the right subtree of T1 is similar to the right subtree of T2.

solution：

```cpp
int similar(BiTree Tl,BiTree T2){
                            //采用递归的算法判断两棵二叉树是否相似
    int leftS,rights;
    if(Tl==NULL&&T2==NULL)  //两树皆空
        return 1;
    else if(Tl==NULLIIT2==NULL)//只有一树为空
        return 0;
    else{
                 //递归判断 
        lefts=similar(Tl->lchild,T2->lchild);
        rightS=similar(Tl->rchild,T2->rchild);
        return leftS&&rightS;
    }
}
```

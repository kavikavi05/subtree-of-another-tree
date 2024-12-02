/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */

typedef struct 
{ 
    int top; 
    int size; 
    struct TreeNode ** stack_arr; 
}stack; 

bool isStackEmpty(stack * Stack) 
{ 
    return ((Stack->top == -1) ? true : false); 
} 

bool isStackFull(stack * Stack) 
{ 
    return ((Stack->top == Stack->size - 1) ? true : false); 
} 

void push(stack * Stack, struct TreeNode * node) 
{ 
    if(isStackFull(Stack)) 
        return; 

    Stack->stack_arr[++(Stack->top)] = node; 
    return; 
} 

struct TreeNode * pop(stack * Stack) 
{ 
    if(isStackEmpty(Stack)) 
        return NULL; 
    return Stack->stack_arr[(Stack->top)--]; 
} 

bool isTreeSame(struct TreeNode * root, struct TreeNode * subroot)
{
    if(!root && !subroot)
        return true;
    else if(!root && subroot)
        return false;
    else if(root && !subroot)
        return false;
    else
    {
        if(root->val != subroot->val)
            return false;

        bool lsubtree_val = isTreeSame(root->left, subroot->left);
        bool rsubtree_val = isTreeSame(root->right, subroot->right);
        return (lsubtree_val & rsubtree_val);
    }
}

bool isSubtree(struct TreeNode* root, struct TreeNode* subRoot) 
{
    bool ret_val = false;

    //Preorder Iterative 
    stack Stack;
    Stack.top = -1;
    Stack.size = 2000;
    Stack.stack_arr = (struct TreeNode **)malloc(sizeof(struct TreeNode *) * Stack.size);

    //Push the root node
    push(&Stack, root);

    while(isStackEmpty(&Stack) == false)
    {
        //Pop the node from the stack and visit it
        struct TreeNode * popNode = pop(&Stack);
        if(popNode->val == subRoot->val)
        {
            ret_val = isTreeSame(popNode, subRoot);
            if(ret_val)
                return ret_val; 
        }

        //If Right Child Present, push it
        if(popNode->right)
            push(&Stack, popNode->right);

        //If Left Child Present, push it
        if(popNode->left)
            push(&Stack, popNode->left);   
    }
    return ret_val;
}

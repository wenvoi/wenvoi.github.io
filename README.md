# wenvoi.github.io
递归知识
最简单的中序遍历
如果需要搜索整颗二叉树，那么递归函数就不要返回值，如果要搜索其中一条符合条件的路径，递归函数就需要返回值，因为遇到符合条件的路径了就要及时返回
数组相关的知识
初始化
 // 初始化二维 dp 数组
  const dp = new Array(m)
  for (let i = 0; i < m; i++) {
    dp[i] = new Array(n).fill(0)
  }
  let res = new Array(m).fill(undefined).map(()=>new Array(n));//二位数组的建立
二叉树
代码随想录
二叉树的前序遍历
C++
 vector<int> preorderTraversal(TreeNode* root) {
       stack<TreeNode*> stk;
       vector<int> res;
       stk.push(root);
       while(!stk.empty()){
           auto p=stk.top();
           stk.pop();
           if(p)res.push_back(p->val);
           else continue;
           stk.push(p->right);
           stk.push(p->left);
       }
       return res;
    }
JS
 if(root===null)return [];
    let stk=[];//js没有站结构只能数组模拟
    let res=[];
    stk.push(root);
    while(stk.length){
        let root =stk.pop();
        res.push(root.val);
        if(root.right!== null){
            stk.push(root.right);
        }
        if(root.left!== null){
            stk.push(root.left);
        }
    }
    return res;
利用p变量来实现
if(root===null)return [];
    let stk=[];
    let res=[];
    stk.push(root);
    while(stk.length){
        let p =stk.pop();
        res.push(p.val);
        if(p.right!== null){
            stk.push(p.right);
        }
        if(p.left!== null){
            stk.push(p.left);
        }
    }
    return res;//中左右
二叉树的中序遍历(递归)
C++
vector<int> res;
    vector<int> inorderTraversal(TreeNode* root) {
        dfs(root);//递归版中序遍历
        return res;
    }
    void dfs(TreeNode* root){
        if(!root)return;
        dfs(root->left);
        res.push_back(root->val);
        dfs(root->right);
    }
JS
递归操作
var inorderTraversal = function(root) {
    let res =[];
    let dfs= (root)=>{//递归的相关方法
        if(!root)return;
        dfs(root.left);
        res.push(root.val);
        dfs(root.right);
    }
    dfs(root);//调用递归方法
    return res;
};
最好不要使用全局变量
提取方法的操作
var inorderTraversal = function(root) {
    var res =[];
    dfs(root,res);
    return res;
};
var dfs=function(root,res){
    if(root=== null)return;
    dfs(root.left,res);
    res.push(root.val);
    dfs(root.right,res);
}
二叉树的后序遍历
C++
JS
if(root === null)return [];
    let stk = [];
    let res = [];
    stk.push(root);
    while(stk.length){
        let p = stk.pop();
        res.push(p.val);
        if(p.left) stk.push(p.left);
        if(p.right) stk.push(p.right);//非递归 先执行右边,在执行左边
    }
    return res.reverse();//中右左顺序 再反转数组就是左右中
二叉树的层次遍历
相关例题：
• 102.二叉树的层序遍历
• 107.二叉树的层次遍历II
• 199.二叉树的右视图
• 637.二叉树的层平均值
• 589.N叉树的前序遍历
C++
if(root==NULL)return {};
        queue<TreeNode*> qu;
        vector<vector<int>> res;//设置二维数组
        qu.push(root);
        while(!qu.empty()){
            int len=qu.size();
            vector<int> link;
            for(int i=0;i<len;i++){
                auto p = qu.front();
                qu.pop();
                link.push_back(p->val);//先插入里面的数组
                if(p->left)qu.push(p->left);
                if(p->right)qu.push(p->right);
            }
            res.push_back(link);
        }
        return res;
    }
JS
let res = new Array(m).fill(undefined).map(()=>new Array(n));//二位数组的建立
var levelOrder = function(root) {
    if(root === null)return [];
    let res = [];
    let qu =[];
    qu.push(root);
    while(qu.length!== 0){
        let len = qu.length;
        // res.push([]);//对你新加进去的这个[] 进行push res[[],]
        let link =[];
        for(let i=0;i<len;i++){
            let p = qu.shift();
            link.push(p.val);
            // res[res.length-1].push(p.val);//就是总是取外面一维数组里面的最后一个空[][[1,2],[*就是往这里面插入数值]]
            if(p.left)qu.push(p.left);
            if(p.right)qu.push(p.right);
        }
        res.push([...link]);//将一维数组导入到二维数组的写法，大致写法一致和C++
    }
    return res;
};

# wenvoi.github.io
---
##递归知识
最简单的中序遍历
如果需要搜索整颗二叉树，那么递归函数就不要返回值，如果要搜索其中一条符合条件的路径，递归函数就需要返回值，因为遇到符合条件的路径了就要及时返回
---
##数组相关的知识
###初始化
 // 初始化二维 dp 数组
 (```)
  const dp = new Array(m)
  for (let i = 0; i < m; i++) {
    dp[i] = new Array(n).fill(0)
  }
  let res = new Array(m).fill(undefined).map(()=>new Array(n));//二位数组的建立
  ---
  (```)
##二叉树
代码随想录
---
##二叉树的前序遍历
C++
(```)
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
    (```)
这里

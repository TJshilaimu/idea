
和图片对应

该仓库有很多的分支，可以通过下面的做法获取所有分支
（案例）
1.克隆仓库
git clone https://github.com/DuYi-Edu/DuYi-Node.git
cd DuYi-Node
2.获取所有远程分支并映射到本地
git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done

### 注意：用git bash可以，但在cmd中会报错，目前没找到问题所在 ###
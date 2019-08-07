## PHP 实现数据结构 加深对数据结构的理解 
#### 数据结构：
    计算机存储，组织数据的方式。数据结构是指相互之间存在一种或多种特定关系的数据元素的集合

#### 数据类型：
    是指一组性质相同的值的集合以及定义在此集合上的一些操作的总称，例如：整型，浮点型，字符型
    分为：
        原子类型，例如：整型，浮点型，字符型
        结构类型，由若干个类型组合而成。
        
#### 抽象：
    是指抽出事物具体的普遍性的本质。它要求抽出问题的特征而忽略非本质的细节。是对具体事物的一个概括。抽象是一种思考问题的方式

#### 抽象数据类型，Abstract Data Type, ADT.
    是指一个数据模型以及定义在该模型上的一组操作
    描述一个抽象数据类型：
        ADT 线性表（List）
        Data 数据对象
        Operation 数据对象上的操作，比如初始化，创建，插入，删除等
        EndData

#### 线性表  (code List/)
    由领个或多个数据元素组成的有限序列
    当有0个元素的线性表称为，空表
#### 线性表 - 顺序存储结构
    指的是一段地址连续的存储单元依次存储线性表的数据元素
    物理上的存储方式就是在内存中，通过占位符形式，把一定内存给占用，然后把相同的数据类型的元素依次放在这块内存当中
#### 树 (code Tree/)
    是n(n>=0)个结点的有限集，当n=0时为空树
    在任意一颗非空树中：
        有且仅有一个特定的 根结点
        当n>1时，其余结点可分为互不相交的有限集，其中每个集合又是一颗树，并成为根的子树
    结点拥有的子树数量，称为结点的度 degree
    树的度 取树内各结点的度的最大值
        度为0的结点称为叶结点(Leaf)或终端结点
        度不为0的结点称为分支结点或非终端结点。除根结点外。分支结点也称为内部结点
    树中结点的最大层次称为树的深度(Depth)或高度
    如果将树中的各个子树看成从左到右是有次序的，不能互换的，则称为树为 有序树，否则称为 无序树
    森林是m颗子树 互不相交的树的集合
#### 二叉树 Binary Tree
    是n (n>=0)个结点的有限集合，该集合为空称为空二叉树
    由一个根结点和两颗互不相交的，分别称为根结点的左子树和由子树的二叉树组成
    特点
        每个结点最多有两颗子树，
        左子树和右子树是又顺序的，次序不能颠倒
        即使树中某结点只有一颗子树，也要区分它是左子树还是右子树
    五种形态
        空二叉树
        只有一个根结点的二叉树
        根结点只有左子树的二叉树
        根结点只有由子树的二叉树
        根结点既有左子树又有右子树的二叉树
    斜树
        要么左右结点都是左子树，要么都是右子树，一条线的斜
    满二叉树
        所有分支结点都有左子树和右子树，并且所有叶子都在同一层，称为满二叉树 
    完全二叉树
        对一颗具有n个结点的二叉树按层序编号，如果编号i(1<=i<=n)的结点与同样深度的满二叉树中的编号i的结点位置完全相同，则称为完全二叉树
    性质：
        在二叉树的第i层上，至多有2^(i-1)个结点，与byte的二进制有点类似
        深度为k的二叉树，至多有2^k - 1个结点(k>=1)，也有byte的二进制有点类似，比如一个字节有符号的最大值0111， 即2^k - 1
        对任何一颗二叉树T，如果其终端结点树为n0，度为2的结点树为n2，则n0 = n2 + 1
        具有n个结点的完全二叉树的深度为 logn的结果向下取整之后 + 1， 2为底数。个人理解 深度k = log(n+1)，2 为底树
    存储结构
        用一维数据存储二叉树中的各个结点，并且结点的存储位置能体现结点之间的逻辑关系，浪费空间
        二叉链表
            每个结点最多两个子结点，所以设计一个结构，包含一个数据域和两个指针域，组成的链表称为二叉链表
    二叉树的遍历
        是指从根结点出发，按照某种次序依次访问二叉树中的所有结点，使得每个结点被访问依次且仅被访问一次
        方式：
            前序遍历
                访问根结点的操作发生在遍历其左右子树之前
                若二叉树为空，则空操作返回，否则先访问根结点，然后前序遍历左子树，在前序遍历右子树，见/images/二叉树遍历-前序遍历.jpeg
            中序遍历
                访问根结点的操作发生在遍历其左右子树之中（间）。
                若树为空，则空操作返回，否则，中序遍历根结点的左子树，然后访问根结点，最后中序遍历右子树
                见/images/二叉树遍历-中序遍历.jpeg
            后序遍历
                访问根结点的操作发生在遍历其左右子树之后。
                若树为空，则空操作返回，否则遍历左子树，然后遍历右子树，最后访问根结点
                见/images/二叉树遍历-后序遍历.jpeg
            层序遍历
                若树为空，则空操作返回，否则从树的第一层，也就是根结点开始访问，从上至下逐层遍历，在同一层中，按从左到右的顺序对结点逐个访问
                见/images/二叉树遍历-层序遍历.jpeg
    线索二叉树 Tree/ClueBinaryTree.php
#### 普通树转为二叉树
> /images/树,二叉树,森林之间的转换.jpeg 图1

    1. 在树中某个根结点的所有子结点之间加一连接
    2. 对这个根结点，除了保留与第一个子结点的连线外，去掉该结点与其他子结点的连线
#### 森林转为二叉树
> /images/树,二叉树,森林之间的转换.jpeg 图2

    ps：森林就是多个树
    1. 先将森林中的每课树变为二叉树，即普通树转为二叉树过程
    2. 在将各个二叉树的跟结点 看作是兄弟结点，从左到右连起来。就形成来一颗二叉树
#### 二叉树转为 树，森林
> /images/树,二叉树,森林之间的转换.jpeg 图3

    1. 若某个结点x是其双亲y的左结点，则将x的右结点，右结点的右结点，。。都与y相连
    2. 去掉所有双亲结点与右结点之间的连线
#### 赫夫曼树
    把这两颗二叉树简化成叶子结点带权的二叉树
    ps: 树结点间的连线相关的数 称为 权(Weight)
    
    结点的路径长度：从根结点到该结点的路径上的连接数
    树的路径长度：树中每个叶子结点的路径长度之和
    结点带权路径长度：结点的路径长度与结点权值的乘积
    树的带权路径长度：WPL（Weighted Path Length ）是树中所有叶子结点的带权路径长度之和
    
    WPL的值越小，说明构造出来的二叉树性能越优
    通过赫夫曼树，如何来构造WPL最小的二叉树？ 图 /images/赫夫曼树构造过程.jpeg
#### 赫夫曼编码
> 编码树如图 /images/赫夫曼树编码树.jpeg

    定长编码：像ASCII编码，约定用8位表示一个字符
    变长编码：单个编码的长度不一致，可以根据整体字符出现频率来调节。比如要发送一个A，就用一个1或0
        这样一个位来表示。约定好这个规则
    前缀码：没有任何码字是其他码字的前缀
    
    
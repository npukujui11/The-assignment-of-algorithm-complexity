### Introduction

#### Dijkstra算法简介

##### 概述

* Dijkstra算法是一种图搜索算法，旨在寻找图中节点之间的最短路径，也是一种求解单源最短路径问题的贪心算法[<sup>[1]</sup>](#refer-anchor-1)。它解决具有非负边路径成本的图的单源最短路径问题，生成最短路径树。由Edsger Dijkstra 构想。

##### 算法条件

* 有向图和无向图

* 所有边都必须具有非负权重
 
* 图必须连接

##### 算法过程

* 将开始的节点称为初始节点。令节点Y的距离为初始节点到Y的距离。Dijkstra算法会分配一些初始距离值，并会尝试逐步改进它们。

  + 1）为每个节点分配一个暂定距离值：对于我们的初始节点将其设置为零，对于所有其他节点将其设置为无穷大。
  
  + 2）标记所有未访问的节点。将初始节点设置为当前节点。创建一组未访问的节点，称为由所有节点组成的未访问集。

  + 3）对于当前节点，考虑其所有未访问的邻居并计算它们的暂定距离。例如，如果当前节点A 的标记距离为6，并且连接它与邻居B的边的长度为 2，则到B（通过 A）的距离将为6+2=8。
  
  + 4）当我们完成对当前节点的所有邻居的考虑后，将当前节点标记为已访问并将其从未访问集中删除。永远不会再次检查已访问的节点。
  
  + 5）如果目的节点已被标记为已访问（规划两个特定节点之间的路径时）或未访问集中节点之间的最小暂定距离为无穷大（规划完整遍历时；发生在初始节点之间没有连接时）和剩余未访问的节点），然后停止。算法已经完成。
  
  + 6）选择标记为最小暂定距离的未访问节点，并将其设置为新的“当前节点”，然后返回步骤 3。 

* 下列图显示了使用Dijkstras算法从节点“a”或“1”到节点“b”或“5”的最短路径。访问过的节点将显示为红色。将会看到最短路径是以最小成本 20 遍历节点1、3、6、5。

  + **目标定义**：给定一个有向图$\mathbf{G={\{N, E\}}}$，其中$\mathbf{N}$是$\mathbf{G}$的节点集合，$\mathbf{E}$是有向边的集合，每条边都有一个非负长度，也可以定义为权重或成本，这些节点中有一个节点被视为源节点。
  
  + **问题定义**：确定从原点到每个节点的最小路径长度。Dijkstra算法使用两组节点$\mathbf{S}$和$\mathbf{C}$，集合$\mathbf{S}$包含选定节点的集合以及给定时间每个节点到原始节点的距离。集合$\mathbf{P}$包含所有尚未被选中且距离未知的候选节点。

  + **算法目标**：计算从集合$\mathbf{S}$中的节点"1"到节点“5”的最短路径

      - **步骤一**：从图$\mathbf{N}$中节点“1”开始；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0026_图层 1.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图1  </p></center>
        </div>

      - **步骤二**：采用广度优先策略从节点“1”的邻接节点$\mathbf{E}$中遍历最短路径；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0025_图层 2.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图2 </p></center>
        </div>

      - **步骤三**：获取到节点“2”的最短路径7，更新集合$\mathbf{S}$中到节点“2”最短路径长度为7；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0024_图层 3.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图3 </p></center>
        </div>

      - **步骤四**：采用广度优先策略从节点“1”的邻接节点$\mathbf{E}$中遍历最短路径；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0023_图层 4.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图4 </p></center>
        </div>

      - **步骤五**：获取到节点“3”的最短路径9，更新集合$\mathbf{S}$中到节点“3”最短路径长度为9；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0022_图层 5.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图5 </p></center>
        </div>

      - **步骤六**：采用广度优先策略从节点“1”的邻接节点$\mathbf{E}$中遍历最短路径；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0021_图层 6.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图6 </p></center>
        </div>

      - **步骤七**：获取到节点“6”的最短路径14，更新集合$\mathbf{S}$中到节点“6”最短路径长度为14；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0020_图层 7.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图7 </p></center>
        </div>

      - **步骤八**：更新节点向量S，向量值表示到该节点的距离，并把节点一移出集合$\mathbf{P}$；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0019_图层 8.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图8 </p></center>
        </div>

      - **步骤九**：结束节点”1“的遍历，接下来从集合$\mathbf{P}$中选择节点“2”开始遍历；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0018_图层 9.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图9 </p></center>
        </div>

      - **步骤十**：从节点“2”的邻接节点中$\mathbf{E}$遍历到节点“3”，发现到节点“3“的距离7+10=17大于向量S中节点”3“的最短距离9；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0017_图层 10.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图10 </p></center>
        </div>


      - **步骤十一**：因此在向量$\mathbf{S}$中不更新节点”3“的最短距离；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0016_图层 11.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图11 </p></center>
        </div>


      - **步骤十二**：接着从节点”2“的$\mathbf{E}$集合进行遍历，遍历到节点”4“；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0015_图层 12.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图12 </p></center>
        </div>

      - **步骤十三**：更新到节点”4“的最短距离7+15=22，更新向量$\mathbf{S}$；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0014_图层 13.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图13 </p></center>
        </div>

      - **步骤十四**：结束从节点”2“开始的遍历，将节点”2“移出集合$\mathbf{P}$；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0013_图层 14.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图14 </p></center>
        </div>

      - **步骤十五**：递归，从节点”1“的$\mathbf{E}$开始广度遍历，从节点”3“开始遍历；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0012_图层 15.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图15 </p></center>
        </div>
      - **步骤十六**：从节点”3“开始遍历，遍历到节点”4“
        <div align=center>
            <img src="picture/Dijkstra_Animation_0011_图层 16.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图16 </p></center>
        </div>
     - **步骤十七**：获得到节点”4“的最短距离9+11=20，小于之前的最短距离22，所以更新到节点”4“的最短距离为20；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0010_图层 17.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图17 </p></center>
        </div>

     - **步骤十八**：遍历到节点”6“；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0008_图层 19.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图18 </p></center>
        </div>

     - **步骤十九**：获得到节点”6“的最短距离9+2=11，小于之前的最短距离14，所以更新到节点”6“的最短距离为11；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0007_图层 20.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图19 </p></center>
        </div>

     - **步骤二十**：结束从节点”3“开始的遍历，将节点”3“移出集合$\mathbf{P}$；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0005_图层 22.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图20 </p></center>
        </div>
    
     - **步骤二十一**：从节点”6“开始遍历，获得到节点”5“的最短路径
        <div align=center>
            <img src="picture/Dijkstra_Animation_0003_图层 24.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图21 </p></center>
        </div>

     - **步骤二十二**：到节点”5“的最短路径11+9=20，更新向量$\mathbf{S}$中的到节点”5“的最短距离
        <div align=center>
            <img src="picture/Dijkstra_Animation_0002_图层 25.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图22 </p></center>
        </div>

     - **步骤二十三**：结束从节点”6“开始的遍历，将节点”6“移出集合$\mathbf{P}$；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0001_图层 26.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图23 </p></center>
        </div>

     - **步骤二十四**：从节点”4“开始的遍历，到节点”5“的最短路径为20+6=26，故有20(4)>=20(5)，无需更新向量$\mathabf{S}$。
        <div align=center>
            <img src="picture/Dijkstra_Animation_0000_图层 27.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图24 </p></center>
        </div>

* **算法思路**：
    + 广度优先；
    + 松弛；


##### 算法时间复杂度

* 每次执行主循环时，都会从队列中提取一个顶点。假设图中有$\mathbf{V}$个顶点，则队列可能包含$\mathbf{O(V)}$个顶点。假定优先级队列的堆实现，每个弹出操作都需要$\mathbf{O(logV)}$时间。所以执行主循环本身所需的总时间是$\mathbf{O(VlogV)}$。

* 此外，我们必须考虑在函数`expand`中花费的时间，它将函数`handle_edge`应用于每个传出边。因为每个顶点只调用一次`expand`，所以每个边只调用一次`handle_edge`。它可能会调用`push(v')`，但在整个执行过程中最多可以有V次这样的调用，因此该`case arm`的总成本最多为$\mathbf{O(VlogV)}$。然而，另一个`case arm`可能被调用$\mathbf{O(E)}$次，并且每次调用 `increase_priority`都需要$\mathbf{O(logV)}$时间来实现堆。



### Reference

<div id="refer-anchor-1"></div>

- [1] Dijkstra, E W. “A Note on Two Problems in Connexion with Graphs.” Numerische Mathematik 1, no. 1 (December 1959): 269–71. doi:10.1007/BF01386390.
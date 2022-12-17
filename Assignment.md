### Introduction

#### Dijkstra算法简介

##### 概述

* Dijkstra算法是一种图搜索算法，它解决具有非负边路径成本的图的单源最短路径问题，生成最短路径树。由Edsger Dijkstra 构想。

##### 算法条件

* 有向图和无向图

* 所有边都必须具有非负权重
 
* 图必须连接

##### 算法过程

* 将开始的节点称为初始节点。令节点Y的距离为初始节点到Y的距离。Dijkstra算法会分配一些初始距离值，并会尝试逐步改进它们。
  + 1）为每个节点分配一个暂定距离值：对于我们的初始节点将其设置为零，对于所有其他节点将其设置为无穷大。
  
  + 2）标记所有未访问的节点。将初始节点设置为当前节点。创建一组未访问的节点，称为由所有节点组成的未访问集。

  + 3）对于当前节点，考虑其所有未访问的邻居并计算它们的暂定距离。例如，如果当前节点 A 的标记距离为 6，并且连接它与邻居 B 的边的长度为 2，则到 B（通过 A）的距离将为 6 + 2 = 8。
  
  + 4）当我们完成对当前节点的所有邻居的考虑后，将当前节点标记为已访问并将其从未访问集中删除。永远不会再次检查已访问的节点。
  
  + 5）如果目的节点已被标记为已访问（规划两个特定节点之间的路径时）或未访问集中节点之间的最小暂定距离为无穷大（规划完整遍历时；发生在初始节点之间没有连接时）和剩余未访问的节点），然后停止。算法已经完成。
  
  + 6）选择标记为最小暂定距离的未访问节点，并将其设置为新的“当前节点”，然后返回步骤 3。 

* 下列图显示了使用 Dijkstras 算法从节点“a”或“1”到节点“b”或“5”的最短路径。访问过的节点将显示为红色。将会看到最短路径是以最小成本 20 遍历节点 1、3、6、5。
  
  + 算法目标：计算从节点“1”到节点“5”的最短路径
      - **步骤一**：从图G中节点“1”开始；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0026_图层 1.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图1  </p></center>
        </div>

      - **步骤二**：采用广度优先策略从节点“1”的邻接节点中遍历最短路径；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0025_图层 2.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图2 </p></center>
        </div>

      - **步骤三**：获取到节点“2”的最短路径7，更新到节点“2”最短路径长度为7；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0024_图层 3.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图3 </p></center>
        </div>

      - **步骤四**：采用广度优先策略从节点“1”的邻接节点中遍历最短路径；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0023_图层 4.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图4 </p></center>
        </div>

      - **步骤五**：获取到节点“3”的最短路径9，更新到节点“3”最短路径长度为9；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0022_图层 5.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图5 </p></center>
        </div>

      - **步骤六**：采用广度优先策略从节点“1”的邻接节点中遍历最短路径；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0021_图层 6.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图6 </p></center>
        </div>

      - **步骤七**：获取到节点“6”的最短路径14，更新到节点“6”最短路径长度为14；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0020_图层 7.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图7 </p></center>
        </div>

      - **步骤八**：更新节点向量S，向量值表示到该节点的距离，并把节点一放入集合P；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0019_图层 8.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图8 </p></center>
        </div>

      - **步骤九**：从节点“1”的邻接节点中的最短距离节点”2“出发，因此结束节点”1“的遍历，接下来从节点“2”开始遍历；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0018_图层 9.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图9 </p></center>
        </div>

      - **步骤十**：遍历到节点“3”，发现到节点“3“的距离7+10=17大于向量S中节点”3“的最短距离9；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0017_图层 10.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图10 </p></center>
        </div>


      - **步骤十一**：不更新节点”3“的最短距离；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0016_图层 11.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图11 </p></center>
        </div>


      - **步骤十二**：接着从节点”2“进行遍历，遍历到节点”4“；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0015_图层 12.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图12 </p></center>
        </div>

      - **步骤十三**：更新到节点”4“的最短距离7+15=22，更新向量S；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0014_图层 13.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图13 </p></center>
        </div>

      - **步骤十四**：结束从节点”2“开始的遍历，将节点”2“放入集合P；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0013_图层 14.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图14 </p></center>
        </div>

      - **步骤十五**：按从节点”1“开始广度遍历，从节点”3“开始遍历，遍历的过程会跳过集合P中的节点；
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

     - **步骤二十**：结束从节点”3“开始的遍历，将节点”3“放入集合P；
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

     - **步骤二十二**：到节点”5“的最短路径11+9=20，更新向量S中的到节点”5“的最短距离
        <div align=center>
            <img src="picture/Dijkstra_Animation_0002_图层 25.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图22 </p></center>
        </div>

     - **步骤二十三**：结束从节点”6“开始的遍历，将节点”6“放入集合P；
        <div align=center>
            <img src="picture/Dijkstra_Animation_0001_图层 26.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图23 </p></center>
        </div>

     - **步骤二十四**：从节点”4“开始的遍历，到节点”5“的最短路径为20+6=26，故有20(4)>=20(5)，无需更新向量S。
        <div align=center>
            <img src="picture/Dijkstra_Animation_0000_图层 27.jpg"
            alt="No Picture"
            style="zoom:100%"/>
            <center><p>图24 </p></center>
        </div>
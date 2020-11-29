# NGSIM(in progress...)

### to be continue... as soon as I finish all the hw ... lol
driving behavior study with NGSIM, visualization, peachtree, intersection

dataset:

FHWA. (2006). NGSIM program peachtree street data. version 1.  
https://catalog.data.gov/dataset/next-generation-simulation-ngsim-vehicle-trajectories  
https://www.opendatanetwork.com/dataset/data.transportation.gov/8ect-6jqj
https://dev.socrata.com/foundry/data.transportation.gov/8ect-6jqj

data format:  

| ﻿Column ID | Column Name   | API Column Name | Data Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------|---------------|-----------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0         | Vehicle_ID    | vehicle_id      | number    | 车辆标识号（按进入部分的时间升序）。重复不关联。                                                                                                                                                                                                                                                                                                                                                                    |
| 1         | Frame_ID      | frame_id        | number    | 帧标识号（按开始时间升序）                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 2         | Total_Frames  | total_frames    | number    | 车辆在此数据集中显示的帧总数                                                                                                                                                                                                                                                                                                                                                                                                    |
| 3         | Global_Time   | global_time     | number    | 自 1970 年 1 月 1 日以来，以毫秒为单位的经过时间。                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 4         | Local_X       | local_x         | number    | 车辆前中心（以英尺）的横向 （X） 坐标与行驶方向的截面最左侧边缘的坐标。                                                                                                                                                                                                                                                                                                                         |
| 5         | Local_Y       | local_y         | number    | 车辆前部中心的纵向（Y）坐标，以英尺为单位，相对于截面在行驶方向上的进入边缘。                                                                                                                                                                                                                                                                                                                        |
| 6         | Global_X      | global_x        | number    | X基于NAD83中的CA State Plane III，车辆前部中心的坐标（以英尺为单位）。属性域值                                                                                                                                                                                                                                                                                                                                                      |
| 7         | Global_Y      | global_y        | number    | Y以NAD83中的CA State Plane III为基础，以英尺为单位的车辆前部中心的坐标。                                                                                                                                                                                                                                                                                                                                                                           |
| 8         | v_length      | v_length        | number    | 车辆长度（以英尺为单位）                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| 9         | v_Width       | v_width         | number    | 车辆宽度（以英尺为单位）                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| 10        | v_Class       | v_class         | number    | 车辆类型：1-摩托车，2-汽车，3-卡车                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 11        | v_Vel         | v_vel           | number    | 车辆以英尺/秒表示的瞬时速度。                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 12        | v_Acc         | v_acc           | number    | 车辆以英尺/秒方块的瞬时加速度。                                                                                                                                                                                                                                                                                                                                                                                                            |
| 13        | Lane_ID       | lane_id         | number    | 车辆的当前车道位置。巷1是最远的左车道;车道 5 是最远的右车道。6号巷是文图拉大道和卡洪加大道的辅道。7号巷是文图拉大道的斜坡，8号巷是卡洪加大道的下坡道。                                                                                                                                                                        |
| 14        | O_Zone        | o_zone          | text      | 车辆的始发区，即车辆进入跟踪系统的位置。研究领域有11个起源，从101到111。有关更多详细信息，请参阅数据分析报告。                                                                                                                                                                                                                              |
| 15        | D_Zone        | d_zone          | text      | 车辆的目的地区域，即车辆退出跟踪系统的位置。研究区有10个目的地，编号从201到211。原点102是一个双向的离场;因此没有关联的目标编号 202。有关更多详细信息，请参阅数据分析报告。                                                                                                                              |
| 16        | Int_ID        | int_id          | text      | 车辆行驶的交叉路口。交叉点编号为 1 到 4，最南端为十字路口 1，研究区最北端为 4。值"0"表示车辆不在交叉路口附近，车辆与兰克希姆大道（Section_ID，下文）的一段相交。有关更多详细信息，请参阅数据分析报告。 |
| 17        | Section_ID    | section_id      | text      | 车辆行驶的部门。Lankershim Blvd 分为五个部分（1 号交叉路口以南;1 号路口和 2 号交叉口、2 号路口和 3 号路口、3 号路口和 4 号路口的北面处）。值"0"表示车辆不认同兰克希姆大道的一段，且车辆位于交叉路口附近（Int_ID）。有关更多详细信息，请参阅数据分析报告
             |
| 18        | Direction     | direction       | text      | 车辆的移动方向。1 - 东行 （EB）， 2 - 北行 （NB）， 3 - 西行 （WB）， 4 - 南行 （SB）。
                                                                                                                                                                                                                                                                                                                                                  |
| 19        | Movement      | movement        | text      | 车辆的移动。1 - 通过 （TH），2 - 左转 （LT）， 3 - 右转 （RT）。
                                                                                                                                                                                                                                                                                                                                                                                     |
| 20        | Preceding     | preceding       | number    | 同一车道上的铅车辆的车辆 ID。值"0"表示没有前一辆车 - 在研究部分结束时发生，由于此数据收集工作只记录了完整的轨迹（研究期间开始时已记录在该部分的车辆未记录）。
                                                                                                                                |
| 21        | Following     | following       | number    | 在同一车道上跟随主题车辆的车辆车辆 ID。值"0"表示没有以下车辆 - 出现在研究部分的开头和 onramp 中，因为此数据收集工作只记录了完整的轨迹（在研究期结束时未穿过该部分下游边界的车辆未记录） |
| 22        | Space_Headway | space_headway   | number    | 空间头在脚。间距提供车辆前中心与前一辆车前中心之间的距离。                                                               |
| 23        | Time_Headway  | time_headway    | number    | 时间进展（以秒为单位）。时间头路提供从车辆前中心（以车辆的速度）到前一辆车的前中心行驶的时间。进展值 99 |
| 24        | Location      | location        | text      | 街道或高速公路名称 |

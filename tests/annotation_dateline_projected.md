```XML

<!--
osgEarth Sample - Annotation going across the dateline.  Should split into multiple features on either side of the earth.
穿越数据线的注释，会在地球每一边切割成多个特征
-->

<!--地图名为readymap.org，类型为投影，默认版本2-->
<map name="readymap.org" type="projected" version="2">

    <!--选项，plate-carre投影-->
    <options>
        <profile>plate-carre</profile>
    </options>

    <!--底层影像名为ReadyMap.org - Imagery，驱动器为TMS-->
    <image name="ReadyMap.org - Imagery" driver="tms">
        <url>http://readymap.org/readymap/tiles/1.0.0/22/</url>
    </image>

    <!--注释-->
    <annotations>

        <!--
        特征名为Flight.Path，空间参考为WGS84
        添加几何体，线段
        样式：黄色（#ffff00）描边，宽度为3，禁用OpenGL光照
        -->
        <feature name="Flight Path">
            <srs>wgs84</srs>
            <geometry>
LINESTRING(140.385 35.765 0, 141.1 35.4917 3944.77, 142.163 35.1617 9645.92, 142.665 35.38 12496.8, 143.872 35.8933 12496.8, 145.667 37.1967 12496.8, 149.825 39.1533 12496.8, 155.668 42.9817 12496.8, 162.31 46.415 13716, 168.783 48.675 13716, 180 50 13716, 190 50 13716, 200 49 13716, 210 48 13716, 220 46 13716, 233 40.625 14935.2, 236.725 39.0533 14935.2, 238.828 37.8333 14935.2, 240.842 36.0417 14935.2, 240.98 35.9133 13819.4, 241.125 35.5133 11087.5, 241.245 35.1833 8832.26, 241.298 35.0317 7798.3, 241.423 34.6833 5419.12, 241.532 34.4967 4063.71, 241.583 34.41 3430.97, 241.73 34.1567 1591.04, 241.59 33.9433 0)
            </geometry>

            <style type="text/css">
                stroke:              #ffff00;
                stroke-width:        3;
                render-lighting:     false;
            </style>
        </feature>

       <!--穿越数据线的影像覆盖，应被切割为两块-->
       <!--An image overlay that crosses the date line and should be split into two chunks-->
        <!--影像覆盖，几何体为四边形-->
        <imageoverlay>
            <url>../data/flag_us.png</url>
            <geometry>POLYGON((170 26, 190 26, 190 56, 170 56))</geometry>
        </imageoverlay>

        <!--轴对齐角的影像覆盖，几何体为四边形-->
        <!--An image overlay with non-axis aligned corners-->
        <imageoverlay>
            <url>../data/flag_us.png</url>
            <geometry>POLYGON((-81 26, -40.5 45, -40.5 75.5, -81 60))</geometry>
        </imageoverlay>


    </annotations>
</map>

```
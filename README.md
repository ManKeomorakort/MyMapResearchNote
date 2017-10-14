# MyMapResearchNote
My Search on Map API

Custom Google Map icon

https://github.com/scottdejonge/map-icons


http://www.i-programmer.info/projects/131-mapping-a-gis/1276-inside-the-kml-placemark.html?start=5

A Polygon generator in Javascript

One of the uses of geometric objects is to create a custom place marker without the need to use a custom bitmap icon. To do this you generally need to generate the KML using a script.
For example to generate an n-sided polygon of radius r and centered on x,y you might use:

function polygon(x,y,r,n){
 var inc=2*Math.PI/n;
 var KML=x.toString()+","+ (r+y).toString()+",0.0\n";
 for (var i = 1; i <n; i++){
  KML=KML + 
    (r*Math.sin(i*inc)+x).toString() +
       "," +
     (r*Math.cos(i*inc)+y).toString()+
        ",0.0\n";
 };

As this only generates the necessary co-ordinates you have to embed it in sutiable KML tags.
For example:
alert(polygon(-1,55,1,3));
generates the co-ordinates for a triangle centered on -1,55 and radius 1.
These can be copied and pasted into the co-ordinate section of a polygon to give:
<Placemark>  
 <Style>
  <LineStyle>
   <color>ff0000ff</color>
   <width>5</width>
  </LineStyle>
  <PolyStyle>
   <color>ff0000ff</color>
  </PolyStyle>
 </Style>
 <Polygon>
  <outerBoundaryIs>
   <LinearRing>
    <coordinates>
      -1,56,0.0
      -0.1339745962155613,54.5,0.0
      -1.8660254037844383,54.5,0.0
      -1,56,0.0
    </coordinates>    
   </LinearRing>
  </outerBoundaryIs>
 </Polygon>
</Placemark>
triangle1
 
You can create any polygon marker in the same way and even approximate a circle if you set n big enough. For example, n=25
circle
 
The reason the "circle" is in fact an ellipse is that we are working with latitude and longitude as if they were measures of linear distance. How much distance a degree of longitude represents depends on the latitude. To make this shape generator position-independent you need to scale the latitude and longitude so that you are working in ground distances - not difficult but something for another article.

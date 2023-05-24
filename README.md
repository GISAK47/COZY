# COZY
var esa = ee.ImageCollection("ESA/WorldCover/v100").first();
//.filterDate('2021-01-01', '2021-12-31');
var vis ={bands:['Map']}; //Map lấy trong thông tin của vệ tinh
//Map.addLayer(esa,vis,'ESA Land Cover');
var esaClip = esa.clip(Ranh);
Map.addLayer(esaClip,vis,'HCM_ESA_LandCover');
Map.centerObject(esaClip);
Export.image.toDrive({
  image:esaClip,
  description: "ESA_HCM",
  scale: 10,
  region: ROI,
  maxPixels: 1e13
});

mapSample
=========

Google Map(V2)のサンプルコードです。（android）



#####Markerを追加

```java
//座標
double latitude = ;
double longitude = ;
 
//marker作成
MarkerOptions marker = new MarkerOptions().position(new LatLng(latitude, longitude)).title("Hello Maps ");
 
// marker追加
googleMap.addMarker(marker);

// 色変更
marker.icon(BitmapDescriptorFactory.defaultMarker(BitmapDescriptorFactory.HUE_ROSE));

```

---------

##### 指定された座標まで移動（アニメーション）
```java
CameraPosition cameraPosition = new CameraPosition.Builder().target(new LatLng(17.385044, 78.486671)).zoom(12).build();
googleMap.animateCamera(CameraUpdateFactory.newCameraPosition(cameraPosition));
```

##### 現在位置の表示
```java
googleMap.setMyLocationEnabled(true); // false to disable
```

#### 【現在位置】取得ボタン
```java
googleMap.getUiSettings().setMyLocationButtonEnabled(true);
```

#### 現在位置を取得
```java
// Getting LocationManager object from System Service LOCATION_SERVICE
LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);

Criteria criteria = new Criteria();

//一番適切なプロバイダーを取得
String provider = locationManager.getBestProvider(criteria, true);

//プロバイダー経由で現在位置を取得
Location location = locationManager.getLastKnownLocation(provider);

//情報が入っていれば、更新！
if(location!=null){
onLocationChanged(location);
}
locationManager.requestLocationUpdates(provider, 20000, 0, this);
```


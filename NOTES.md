# Notes on the Dataset

## Data Format

The dataset is arranged by frames. Each frame combines image (`waymo_open_dataset.dataset_pb2.CameraImage`), range image, lidar, and other data at the same timestamp.

### Camera Image
Camera Image: Camera images are taken using the stero cameras surrounding the vehicle.

### Range Image
Range Image: A range image is typically a 2D grid where each pixel represents a depth measurement from a specific viewpoint. This depth information is often obtained using depth sensors like LiDAR (Light Detection and Ranging) or depth cameras. Each pixel in the range image corresponds to a specific direction or angle from the sensor, and the value of each pixel represents the distance to the nearest object in that direction.

### Point Cloud
Point Cloud: Point cloud data, on the other hand, represents a collection of 3D points in space, where each point has its own x, y, and z coordinates. In the dataset, the point cloud is converted from range image.

## Label Format

Each frame has a `frame.camera_labels` (type `google.protobuf.pyext._message.RepeatedCompositeContainer`). This `frame.camera_labels` can contain any number of 'labels' (of class `waymo_open_dataset.label_pb2.Label`) of the following form:

```
box {
  center_x: 1875.489705
  center_y: 821.69859
  width: 262.10984999999994
  length: 89.02059000000008
}
type: TYPE_VEHICLE
id: "2b47a269-226d-4cde-b880-8f100246c1f5"
```

These 'labels' also are under the category of [`FRONT`, `FRONT_LEFT`, `SIDE_LEFT`, `FRONT_RIGHT`, `SIDE_RIGHT`] indicating which camera they are picked from.
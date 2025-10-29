```
esphome:
  name: esp32-camera-rtsp

esp32:
  board: esp32-s3-devkitc-1
  variant: esp32p4

# Caméra + Encodeurs
mipi_dsi_cam:
  - id: my_camera
    sensor: sc202cs
    i2c_id: bus_a
    enable_h264_encoder: true

h264:
  id: h264_enc
  camera_id: my_camera
  bitrate: 3000000  # 3 Mbps pour bonne qualité
  gop_size: 30

# Serveur RTSP
rtsp_server:
  h264_encoder_id: h264_enc
  port: 8554
  path: "/camera"
```  

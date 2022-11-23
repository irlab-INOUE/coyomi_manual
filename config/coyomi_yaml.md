# coyomi.yaml の設定
以下に`coyomi.yaml`の設定例を示します．
特に，`arrived_check_distance` の値は走行安定性に大きく影響します．
狭い屋内通路では`1.0`，学校内やつくばチャレンジのような
環境では`2.0`程度でうまく行きます．


```yaml
Robot_name: Coyomi

Size:
  width: 700      #[mm]
  length: 700     #[mm]
  height: 1200    #[mm]
  weight: 70      #[kg]

MapPath:
  -
    path: map/RWRC2022_1022_one
    occupancy_grid_map: occMap.png
    map_RGBA: map_RGBA.png
    way_point: wp.txt
    likelyhood_field: lfm.txt
    mapInfo: mapInfo.yaml

MotionControlParameter:
  velocity_down_coefficient: 0.9      # [未使用]単位なし
  back_velocity: 0.4                  # [未使用][m/s]
  arrived_check_distance: 2.0         # [m] RWRCでは2.0がよさそう
  auto_loop: false                    # [未使用]ゴール地点で自動でループするか．false:キー入力を待つ

DWA:    # Dynamic Window Approach parameters
  limit_distance: 1.0         # [m] 障害物との距離の制限
  dv: 0.02                    # [m/s] DWの速度分解能
  dw: 0.04                    # [rad/s] DWの角速度分解能
  acceleration_limit: 1.0     # [m/s^2]
  w_acceleration_limit: 140   # [deg/s^2]
  T: 1.0                      # [s] 評価する時間
  v_max: 1.2                  # [m/s] DWの速度の上限値
  v_min: 0.0                  # [m/s] DWの速度の下限値
  w_max: 80.0                 # [deg/s] DWの角速度の上限値
  w_min: -80.0                # [deg/s] DWの角速度の下限値
  path_divided_step: 10       # pathを離散化するステップ T/path_diveded_step
  alpha: 2.0                  # heading weight
  beta: 0.5                   # distance weight
  gamma: 0.5                  # velocity weight
  obstacle_size: 0.5          # [m] 障害物から離れる距離
```

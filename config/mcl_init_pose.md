# MCLの初期姿勢の設定
現状ではナビゲーション開始時点において大域的自己位置推定は実装していないため，パーティクル集合の初期配置は
明示的に与える必要があります．

`$COYOMI_NAVI/src/`Navigation.cpp`の次の場所で設定してください．

```cpp
Pose2d init_pose(8.0,  0.0, 0);  // 左スタートMCL の初期姿勢
```

与える引数はグローバル座標系における$x$[m], $y$[m], $\theta$[rad] の実数値です．

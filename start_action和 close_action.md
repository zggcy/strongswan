# start_action 

strongSwan 中关于 start_action 解释：

<img src=".//assets/start_action和 close_action.assets/start_action-5855930.png" alt="start_action" style="zoom:50%;" />

> [!IMPORTANT]
>
> 仅限当前配置文件被首次加载的时，才会触发这个start_action。如果对端或者本端手动关闭，执行 `swanctl --load-all`重新加载同一个配置文件，`start_action`则不会生效。

1. start_action=start

​	加载配置文件时，自动建立隧道。

<img src="./assets/start_action和 close_action.assets/image-20250822174919942.png" alt="image-20250822174919942" style="zoom:50%;" />

2. start_action = trap

​	加载配置文件，自动安装 policy 策略

<img src="./assets/start_action和 close_action.assets/image-20250822175053324-5856259.png" alt="image-20250822175053324" style="zoom:50%;" />

3. start_action=none

​	加载配置文件不会执行任何操作。



# close_action

strongSwan 中关于 close_action 解释：

<img src="./assets/start_action和 close_action.assets/image-20250822180122105-5856888.png" alt="image-20250822180122105" style="zoom:50%;" />

> [!CAUTION]
>
> Action to perform after a CHILD_SA gets closed by the peer. 当且仅当对端用户关闭连接才可执行 close_action。

1. close_action=start

   当对端端关闭掉CHILD_SAs（或IKE_SAs）后，本端会直接重新建立。

<img src="./assets/start_action和 close_action.assets/image-20250822180459157-5857101.png" alt="image-20250822180459157" style="zoom:50%;" />


2. close_action = trap
当CHILD_SAs（或IKE_SAs）被对端关闭时，本端会保留policy 策略。

<img src="./assets/start_action和 close_action.assets/image-20250822180930520-5857372-5857376.png" alt="image-20250822180930520" style="zoom: 50%;" />

3. close_action=none

​	对端关闭隧道，本端不执行任何操作。

# AW31N docker compile example

This is a example of compiling AW31N project with docker.

The example uses the `transfer` demo in the `AW31N_SDK`.

## Usage

1. Pull the AW31N SDK docker

   ```bash
   docker pull ghcr.io/volwaves/aw31n-sdk:latest
   ```
2. Run the command below in the directory of the `transfer` folder. 

   ```bash
   docker run --rm \
   -v $(pwd)/transfer:/SDK/apps/docker/transfer \
   ghcr.io/volwaves/aw31n-sdk:latest /bin/bash -c "cd transfer/board/bd47 && make && cp -f /SDK/apps/app/post_build/bd47/update.ufw /SDK/apps/docker/transfer/post_build/"
   ```

	1. The command will create a `aw31n-sdk` container with the `transfer` folder mounted at the ready to compile path in the container.  
	2. Then, the tranfer demo will be compiled in the container.  
	3. Finally, the firmware would be copied out.

> [!TIP]
> In practice, you should change `transfer` to your actual project folder name.

3. The compiled firmware `update.ufw` would be copied into `transfer/post_build` as below.
   ```tree
   transfer
   ├── board
   ├── config
   ├── examples
   ├── include
   ├── modules
   ├── post_build
   │   └── update.ufw	<---- compiled firmware here!!!
   ├── app_main.c
   └── version.c
   ```

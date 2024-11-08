# knockd-iptables

Opens port on ALL interfaces for IP that knocks correctly.

## Usage

### Standard usage

```bash
sudo docker run \                                            
  --net=host \
  --privileged \
  --name knockd \
  -d \
  -e KNOCKD_SEQUENCE=SEQUENCE_OF_PORT_KNOCKS \
  -e KNOCKD_PORTS=PORTS_THAT_WILL_OPEN \
  -e KNOCKD_INTERFACE=INTERFACE_WHERE_WE_LISTEN_FOR_KNOCKS \
  knockd
```

### Secrets file usage

```bash
sudo docker run \                                            
  --net=host \
  --privileged \
  --name knockd \
  -d \
  -e KNOCKD_SEQUENCE_FILE=PATH_TO_FILE \
  -e KNOCKD_PORTS_FILE=PATH_TO_FILE \
  -e KNOCKD_INTERFACE_FILE=PATH_TO_FILE \
  knockd
```

Useful in compose files.

## Example

### Standard example

```bash
sudo docker run \                                            
  --net=host \
  --privileged \
  --name knockd \
  -d \
  -e KNOCKD_SEQUENCE="7000,8000,9000" \
  -e KNOCKD_PORTS="22,33,44" \
  -e KNOCKD_INTERFACE="eth0" \
  knockd
```

### Secrets file example

```bash
sudo docker run \
  --net=host \
  --privileged \
  --name knockd \
  -d \
  -e KNOCKD_SEQUENCE_FILE=/run/secrets/knockd_sequence \
  -e KNOCKD_PORTS_FILE=/run/secrets/knockd_ports \
  -e KNOCKD_INTERFACE_FILE=/run/secrets/knockd_interface \
  knockd
```

## Other things to keep in mind

You might want to allow established connections:
```bash
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

## Contribute

https://github.com/ppavacic/knockd/
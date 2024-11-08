# knockd-iptables

## Usage

### Standard usage

```bash
docker run --net=host --privileged --name knockd -d ppavacic/knockd \
-e KNOCKD_SEQUENCE=SEQUENCE \
-e KNOCKD_PORTS=PORTS \
-e KNOCKD_INTERFACE=INTERFACE
```

### Secrets file usage

```bash
docker run --net=host --privileged --name knockd -d ppavacic/knockd \
-e KNOCKD_SEQUENCE_FILE=SEQUENCE_FILE \
-e KNOCKD_PORTS_FILE=PORTS_FILE \
-e KNOCKD_INTERFACE_FILE=INTERFACE_FILE
```

If INTERFACE is empty, will listen to all available interfaces.

## Example

### Standard example

```bash
docker run --net=host --privileged --name knockd -d ppavacic/knockd \
-e KNOCKD_SEQUENCE="7000,8000,9000" \
-e KNOCKD_PORTS="22,33,44" \
-e KNOCKD_INTERFACE="eth0"
```

### Secrets file example

```bash
docker run --net=host --privileged --name knockd -d ppavacic/knockd \
-e KNOCKD_SEQUENCE_FILE=/run/secrets/knockd_sequence \
-e KNOCKD_PORTS_FILE=/run/secrets/knockd_ports \
-e KNOCKD_INTERFACE_FILE=/run/secrets/knockd_interface
```

## Contribute

https://github.com/ppavacic/knockd/
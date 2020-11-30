# service_mesh_with_consul_and_envoy

socat -v tcp-l:8181,fork exec:"/bin/cat"
consul agent -dev -config-dir=./consul.d -node=machine
consul connect envoy -sidecar-for web -admin-bind localhost:19000
consul connect envoy -sidecar-for socat -admin-bind localhost:19001
nc 127.0.0.1 9191


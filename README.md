# Raspberry Pi Monitor
Permite monitorizar distintos parámetros de una Raspberry Pi, temperatura, uso CPU..., a través de un navegador

Se utilizan los servicios:
- Prometheus
- Grafana
- cAdvisor
- NodeExporter

# Instalación
- Crear la carpeta data para Prometheus y Grafana
    ```bash
    mkdir -p prometheus/data grafana/data && \
    sudo chown -R 472:472 grafana/ && \
    sudo chown -R 65534:65534 prometheus/
    ```
- Iniciar con `docker compose up -d --build`
- Acceder a Grafana Dashboard mediante navegador: `http://<ip>:3000`
    - Usuario y contraseña por defecto: `admin`. Se solicitará la contraseña nueva en el primer inicio de sesión
- Activar contabilidad de memoria y swap (***\*Opcional***)
    ```bash
    sudo sed -i 's/^GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1 swapaccount=1"/' /etc/default/grub
    sudo update-grub
    sudo reboot
    ```

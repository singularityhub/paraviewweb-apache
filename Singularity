Bootstrap: docker
From: kitware/paraviewweb:pvw-base-v5.6.0

# sudo singularity build paraview-web.simg Singularity
# mkdir /tmp/apache2
# sudo singularity instance.start --bind /tmp/apache2:/var/run/apache2 paraview-web.simg apache
# sudo singularity instance start --bind /tmp/apache2:/var/run/apache2 paraview-web.simg apache # v3.0 and up

# singularity instance.list
# DAEMON NAME      PID      CONTAINER IMAGE
# apache           13743    /home/vanessa/Documents/Dropbox/Code/shub/containers/apache/paraview-web.simg

%files
    config/website/ /var/www/html/
    config/launcher/launcher-template.json /opt/wslink-launcher/launcher.json

%post
    /bin/bash /opt/paraviewweb/scripts/addEndpoints.sh glance /opt/paraview/install/share/paraview-5.6/web/glance/www
    /bin/bash /opt/paraviewweb/scripts/addEndpoints.sh lite /opt/paraview/install/share/paraview-5.6/web/lite/www
    /bin/bash /opt/paraviewweb/scripts/addEndpoints.sh divvy /opt/paraview/install/share/paraview-5.6/web/divvy/www
    /bin/bash /opt/paraviewweb/scripts/addEndpoints.sh visualizer /opt/paraview/install/share/paraview-5.6/web/visualizer/www
    mkdir -p /var/run/apache2

%startscript
    exec /opt/paraviewweb/scripts/start.sh

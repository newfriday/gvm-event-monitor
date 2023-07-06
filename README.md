*   gvm-event-monitor is an example for libvirt event loop, it serve as a json rpc server, meanwhile, it run a event loop to monitor libvirt event.
*   compile:

        ./gvm-conf.sh -a
*   install service:

        cp build/gvm-event-monitor /usr/bin/
        cp gvm-event-monitor.service /usr/lib/systemd/system/
*   start service:

        systemctl start gvm-event-monitor.service
*   test helloworld json rpc:

        echo "{\"method\": \"helloworld\", \"params\": {\"action\": \"fake_action\", \"request_id\": \"fake_request_id\"}, \"id\": \"FAKE_ID\" }" | nc  localhost 12190
        systemctl status gvm-event-monitor.service
*   to test event monitor, just employ service on host which can launch a vm with libvirt, starting a vm and peer the output of the service like:

        systemctl status gvm-event-monitor.service

## Deploy Employee Portal cells with CNAB 
    #Set Duffle repo location
    export DUFFLE_HOME=$(pwd)/.duffle


    # Build hr,employee and stock-options cells
    duffle build hr
    duffle build employee
    duffle build stock-options

    # Change the kube-conf.yaml to point to the K8S config file and add as a duffle credential
    duffle credentials add kube-conf.yaml

    # View Bundles
    duffle bundles list

    # Install
    duffle install stock1 stock-options -c kube-conf
    duffle install employee1 employee -c kube-conf
    duffle install hr1 hr -c kube-conf --set stock-cell-name=stock1 --set employee-cell-name=employee1

    # Status
    duffle status stock1 -c kube-conf
    duffle status employee1 -c kube-conf
    duffle status hr1 -c kube-conf

    # Uninstall
    duffle uninstall stock1 -c kube-conf
    duffle uninstall employee1 -c kube-conf
    duffle uninstall hr1 -c kube-conf

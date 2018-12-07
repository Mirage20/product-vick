
    #Set Duffle repo location
    export DUFFLE_HOME=$(pwd)


    # Build hr,employee and stock-options cells
    duffle build hr
    duffle build employee
    duffle build stock-options

    # Change the kube-conf.yaml and add as a duffle credential
    duffle credentials add kube-conf.yaml

    # View Bundles
    duffle bundles list

    # Install
    duffle install stocks stock-options -c kube-conf

    # Status
    duffle status stocks -c kube-conf

    # Uninstall
    duffle uninstall stocks -c kube-conf

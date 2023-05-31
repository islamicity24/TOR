```
gcloud compute instance-templates create virtualcity-instance-template-1 --project=dashboard-project-3***11 --machine-type=e2-micro --network-interface=network=default,network-tier=PREMIUM --maintenance-policy=MIGRATE --provisioning-model=STANDARD --service-account=7***95626487-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --create-disk=auto-delete=yes,boot=yes,device-name=virtualcity-instance-template-1,image=projects/debian-cloud/global/images/debian-11-bullseye-v20230509,mode=rw,size=10,type=pd-balanced --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --reservation-affinity=any
```

```
gcloud beta compute instance-groups managed create virtualcity-instance-group-1 --project=dashboard-project-3***11 --base-instance-name=virtualcity-instance-group-1 --size=1 --template=virtualcity-instance-template-1 --zone=asia-southeast2-a --list-managed-instances-results=PAGELESS --no-force-update-on-repair 

gcloud beta compute instance-groups managed set-autoscaling virtualcity-instance-group-1 --project=dashboard-project-3***11 --zone=asia-southeast2-a --cool-down-period=73 --max-num-replicas=3 --min-num-replicas=1 --mode=on --target-cpu-utilization=0.6
```

![image](https://github.com/islamicity24/TOR/assets/126258837/df590d17-0c4c-47aa-82d6-db9ab61aa3df)


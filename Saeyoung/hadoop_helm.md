```helm fetch stable/hadoop
helm install --set yarn.nodeManager.resources.limits.memory=4096Mi --set yarn.nodeManager.replicas=1 stable/hadoop --tls

kubectl exec -n default -it lumpy-narwhal-hadoop-hdfs-nn-0 -- /usr/local/hadoop/bin/hdfs dfsadmin -report
kubectl exec -n default -it lumpy-narwhal-hadoop-yarn-rm-0 -- /usr/local/hadoop/bin/yarn node -list
kubectl exec -n default -it lumpy-narwhal-hadoop-yarn-nm-0 -- /usr/local/hadoop/bin/hadoop jar /usr/local/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-client-jobclient-2.9.0-tests.jar TestDFSIO -write -nrFiles 5 -fileSize 128MB -resFile /tmp/TestDFSIOwrite.txt
kubectl exec -n default -it lumpy-narwhal-hadoop-yarn-rm-0 -- /usr/local/hadoop/bin/mapred job -list

helm fetch stable/zeppelin
helm install --namespace default --set hadoop.useConfigMap=true,hadoop.configMapName=lumpy-narwhal-hadoop stable/zeppelin --tls
```

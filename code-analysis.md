Scheduling, Batching, Binpacking, Launch decsion

karpenter-provider-alicloud/cmd/controller/main.go
WithControllers(ctx, corecontrollers.NewControllers(

karpenter/pkg/controllers/controllers.go
return []controller.Controller{
        p, evictionQueue, disruptionQueue,
        disruption.NewController(clock, kubeClient, p, cloudProvider, recorder, cluster, disruptionQueue),
        provisioning.NewPodController(kubeClient, p),
        provisioning.NewNodeController(kubeClient, p),
        nodepoolhash.NewController(kubeClient),
        expiration.NewController(clock, kubeClient),
        informer.NewDaemonSetController(kubeClient, cluster),

karpenter-provider-alicloud/vendor/sigs.k8s.io/controller-runtime/pkg/manager/runnable_group.go
func (r *runnableGroup) Start(ctx context.Context) error {
        go r.reconcile()

karpenter-provider-alicloud/vendor/sigs.k8s.io/controller-runtime/pkg/reconcile/reconcile.go
func (a *objectReconcilerAdapter[T]) Reconcile(ctx context.Context, req Request) (Result, error) {
        return a.objReconciler.Reconcile(ctx, o)

karpenter/pkg/controllers/provisioning/controller.go
c.provisioner.Trigger()

karpenter/pkg/controllers/provisioning/provisioner.go
p.batcher.Wait(ctx)
p.cluster.Synced
results, err := p.Schedule(ctx)
s, err := p.NewScheduler(ctx, pods, nodes.Active())
instanceTypeOptions, err := p.cloudProvider.GetInstanceTypes(ctx, lo.ToPtr(nodePool))

karpenter/pkg/controllers/provisioning/scheduling/scheduler.go
s.calculateExistingNodeClaims(stateNodes, daemonSetPods)


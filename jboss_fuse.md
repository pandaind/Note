### General Karaf Shell Commands:

- `help` – List all available commands.
- `version` – Show the current version of JBoss Fuse.
- `list` – List all running bundles.
- `shutdown` – Shut down the JBoss Fuse container.
- `log:display` – Display recent log entries.
- `log:tail` – Stream live log entries to the console.

### Bundle Management:

- `bundle:install <URL>` – Install a new bundle from a URL.
- `bundle:start <bundle-ID>` – Start a bundle.
- `bundle:stop <bundle-ID>` – Stop a running bundle.
- `bundle:restart <bundle-ID>` – Restart a bundle.
- `bundle:uninstall <bundle-ID>` – Uninstall a bundle.
- `bundle:list` – List all bundles and their statuses.
- `bundle:diag <bundle-ID>` – Diagnose problems with a specific bundle.

### Features (Feature Management):

- `feature:list` – List available features.
- `feature:install <feature-name>` – Install a feature.
- `feature:uninstall <feature-name>` – Uninstall a feature.
- `feature:repo-add <URL>` – Add a feature repository.
- `feature:repo-list` – List all added feature repositories.

### Camel Commands (Apache Camel Management):

- `camel:context-list` – List all Camel contexts.
- `camel:route-list` – List all Camel routes.
- `camel:route-start <route-ID>` – Start a Camel route.
- `camel:route-stop <route-ID>` – Stop a Camel route.
- `camel:route-info <route-ID>` – Display information about a specific route.
- `camel:context-stop <context-name>` – Stop a specific Camel context.

### OSGi Commands:

- `osgi:install <URL>` – Install a new OSGi bundle.
- `osgi:start <bundle-ID>` – Start an OSGi bundle.
- `osgi:stop <bundle-ID>` – Stop an OSGi bundle.
- `osgi:list` – List all OSGi bundles.
- `osgi:headers <bundle-ID>` – Display OSGi bundle headers.

### Fabric (Fabric8-based Commands):

- `fabric:create` – Create a new Fabric container.
- `fabric:container-list` – List all containers in the Fabric.
- `fabric:container-create-child` – Create a child container in the Fabric.
- `fabric:join <zookeeper-URL>` – Join an existing Fabric.
- `fabric:profile-list` – List all Fabric profiles.
- `fabric:profile-edit` – Edit a Fabric profile.

### Monitoring and Health:

- `jmx:list` – List available JMX beans.
- `jmx:get <bean-name>` – Get attributes of a specific JMX bean.
- `dev:watch` – Watch for file changes and redeploy bundles automatically.
- `dev:dump-create` – Create a thread dump.

### Deployment Commands:

- `admin:start` – Start a managed container.
- `admin:stop` – Stop a managed container.
- `admin:list` – List managed containers.

---

### Advanced OSGi Commands:

- `osgi:refresh <bundle-ID>` – Refresh a bundle and update its dependencies.
- `osgi:resolve <bundle-ID>` – Resolve a bundle if its dependencies are satisfied.
- `osgi:framework-wiring` – Display framework wiring information.
- `osgi:requirements` – Show bundle requirements.
- `osgi:capabilities` – Display capabilities offered by a bundle.
- `osgi:bundle-level <level>` – Set the start level for a specific bundle.
- `osgi:start-level <level>` – Change the OSGi framework’s start level.

### Advanced Feature Management:

- `feature:refresh <feature-name>` – Refresh a feature (reapply features).
- `feature:install --no-auto-refresh <feature-name>` – Install a feature without refreshing dependent bundles.
- `feature:uninstall --force <feature-name>` – Force uninstall a feature, even if it has dependencies.
- `feature:info <feature-name>` – Get detailed information about a feature.

### Fabric Management (Fabric8-Related Commands):

- `fabric:cluster-list` – List all clusters within the Fabric.
- `fabric:profile-create --parent <profile-name>` – Create a new Fabric profile with a parent.
- `fabric:container-upgrade <container>` – Upgrade a container to the latest version.
- `fabric:ensemble-add` – Add a new container to the Fabric ensemble.
- `fabric:ensemble-remove` – Remove a container from the Fabric ensemble.
- `fabric:patch-list` – List all available patches in the Fabric.
- `fabric:patch-apply <patch-name>` – Apply a patch to the Fabric.
- `fabric:patch-install <patch-name>` – Install a patch in the Fabric without applying it.

### Advanced Camel Commands:

- `camel:context-info <context-name>` – Display advanced information about a Camel context.
- `camel:endpoint-list` – List all endpoints in Camel contexts.
- `camel:endpoint-info <endpoint-uri>` – Display information about a specific Camel endpoint.
- `camel:route-reset-stats <route-ID>` – Reset performance stats for a specific Camel route.
- `camel:context-dump <context-name>` – Export the full configuration of a Camel context.
- `camel:tracer-start` – Start the Camel tracer for tracking exchanges.
- `camel:tracer-stop` – Stop the Camel tracer.
- `camel:profiler-start` – Start profiling for Camel routes.
- `camel:profiler-stop` – Stop profiling for Camel routes.

### Advanced Karaf Commands:

- `dev:dynamic-import <package>` – Dynamically import a Java package into OSGi at runtime.
- `dev:classloaders` – Show classloaders used by bundles.
- `config:edit <PID>` – Edit the configuration of a bundle or service with the given PID.
- `config:propappend <PID> <key> <value>` – Append a new value to an existing configuration property.
- `config:proplist <PID>` – List all configuration properties for a bundle/service.
- `config:update` – Apply updates to configuration after editing.
- `jaas:realm-list` – List all available security realms.
- `jaas:user-add <realm>` – Add a user to a specific security realm.
- `jaas:user-delete <realm>` – Remove a user from a realm.

### JMX and Monitoring Commands:

- `jmx:set <bean-name> <attribute> <value>` – Set the value of a JMX attribute.
- `jmx:invoke <bean-name> <operation>` – Invoke an operation on a JMX MBean.
- `jmx:subscribe <bean-name>` – Subscribe to notifications from a JMX MBean.
- `jmx:unsubscribe <subscription-ID>` – Unsubscribe from JMX notifications.
- `jmx:poll <bean-name> <interval>` – Poll a JMX attribute at a given interval.

### System Management Commands:

- `shell:info` – Display detailed system information including Java, OS, and memory usage.
- `system:property` – Display Java system properties.
- `system:property-set <key> <value>` – Set a Java system property.
- `system:shutdown --force` – Forcefully shutdown the JBoss Fuse container.
- `thread:dump` – Generate a thread dump of the JVM.
- `dev:gc` – Trigger a garbage collection manually.

### Deployment and Provisioning:

- `admin:create <container-name>` – Create a new managed container.
- `admin:destroy <container-name>` – Destroy a managed container.
- `admin:connect <container-name>` – Connect to a remote container.
- `admin:status <container-name>` – Get the status of a remote container.
- `admin:change-opts <container-name> <options>` – Change the Java options for a container.

### Performance and Profiling:

- `profiling:agent-start <PID>` – Start profiling a specific bundle or service.
- `profiling:agent-stop <PID>` – Stop profiling a bundle or service.
- `metrics:list` – List metrics available for the system.
- `metrics:display <metric-name>` – Display a specific metric.

### Debugging and Troubleshooting:

- `trace:start <PID>` – Start tracing activity for a specific process or bundle.
- `trace:stop <PID>` – Stop tracing.
- `trace:status` – Display current tracing status.
- `tracer:dump` – Dump trace logs for further analysis.
- `jaas:role-add` – Add a new role to a user.

### Patch Management:

- `patch:add <patch-name>` – Add a new patch to the container.
- `patch:list` – List all patches in the system.
- `patch:install <patch-name>` – Install a patch into the system.
- `patch:rollback <patch-name>` – Rollback a previously applied patch.

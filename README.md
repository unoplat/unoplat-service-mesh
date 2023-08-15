### Version: 1.2.11-dev

1. **Enabled gossip encryption with automatic key generation.**
   - Description: Secured internal Consul communication by enabling encryption for gossip protocol. Keys are generated automatically, enhancing security without manual intervention.

2. **Enabled TLS across the Consul cluster.**
   - Description: Enhanced security by enabling Transport Layer Security (TLS) for encrypted communication within the Consul cluster.

3. **Enabled auto-encryption for Consul clients.**
   - Description: Consul clients now automatically encrypt their communication, ensuring secure interactions without manual configuration.

4. **Storage for consul servers for dev envs kept to 5gbs.**
   - Description: Set a storage limit of 5GB for Consul servers in development environments, optimizing resource usage.

5. **StorageClass kept to civo volume.**
   - Description: Specified the storage class for persistent volumes as "civo volume", ensuring compatibility with the Civo Kubernetes platform.

6. **Consul server limit cpu increased to 450m.**
   - Description: Boosted the CPU resource limit for Consul servers to 450 milliCPUs, enhancing performance.

7. **Changed cpu spec limit for consul agents to 450m.**
   - Description: Updated the CPU resource limit for Consul agents to 450 milliCPUs, ensuring optimal agent performance.

8. **Enabled CNI.**
   - Description: Activated the Container Network Interface (CNI) for better network configuration and traffic management in the Consul service mesh.

9. **Changed cpu spec limit for cni to 400m and memory to 200 Mi.**
   - Description: Adjusted resource limits for CNI, setting CPU to 400 milliCPUs and memory to 200 MiB, optimizing CNI performance.

10. **Changed cpu spec limit for connect inject to 250m.**
   - Description: Updated the CPU resource limit for the connect injector to 250 milliCPUs, ensuring efficient service mesh injections.

11. **Modified sidecar proxy cpu request, cpu limit, memory request, and memory limit to 100 m, 250m, 100Mi, and 200Mi respectively.**
   - Description: Fine-tuned resource requests and limits for sidecar proxies, optimizing their performance and resource usage.

12. **Modified initContainer cpu limit to 250m.**
   - Description: Adjusted the CPU resource limit for initialization containers to 250 milliCPUs, ensuring a smooth startup process.

13. **Modified resources for ingress gateways. Cpu limit to 250m and memory limit to 200Mi.**
   - Description: Updated resource limits for ingress gateways, optimizing their performance when handling incoming traffic.

14. **Enabled agent and client metrics.**
   - Description: Activated metrics collection for Consul agents and clients, providing insights into their performance and behavior.

15. **Enabled aggregated metrics.**
   - Description: Activated the collection of aggregated metrics, offering a consolidated view of performance metrics across the cluster.

16. **Enable UI metrics.**
   - Description: Activated metrics visualization in the Consul User Interface (UI), providing a graphical representation of performance metrics.


### Consul Components Overview

#### 1. **Gossip Encryption**
- **Description**: Gossip protocol is used by Consul for internal communication to discover other nodes and check their health. Encryption ensures that this communication is secure.
- **Interaction**: All nodes in the Consul cluster use the gossip protocol to communicate with each other. Automatic key generation ensures that these nodes can securely join the cluster without manual key distribution.

#### 2. **TLS (Transport Layer Security)**
- **Description**: TLS provides encrypted communication within the Consul cluster, ensuring data confidentiality and integrity.
- **Interaction**: All components of the Consul cluster (servers, clients, and agents) use TLS to securely communicate with each other.

#### 3. **Auto-Encryption**
- **Description**: Allows Consul clients to automatically encrypt their communication.
- **Interaction**: When a new Consul client joins the cluster, it requests an encrypted certificate from the Consul servers, ensuring secure communication without manual certificate management.

#### 4. **Consul Servers Storage**
- **Description**: Consul servers store the cluster's state, configuration, and metadata.
- **Interaction**: Agents communicate with servers to register services, report health checks, and retrieve configuration.

#### 5. **StorageClass**
- **Description**: Defines the type of storage used in Kubernetes. "civo volume" is specific to the Civo Kubernetes platform.
- **Interaction**: Used by Consul servers to store persistent data.

#### 6. **Consul Server**
- **Description**: Consul servers are the primary components that store the cluster's state and handle queries.
- **Interaction**: Agents communicate with servers for service discovery, configuration, and other cluster-wide functionalities.

#### 7. **Consul Agents**
- **Description**: Agents run on every node in the Consul cluster, handling local service registration, health checking, and forwarding queries to servers.
- **Interaction**: Agents communicate with servers and other agents. They also interact with services running on their local node.

#### 8. **CNI (Container Network Interface)**
- **Description**: CNI is a standard used by Kubernetes for pod networking. Consul's CNI plugin sets up the necessary network configurations for service mesh traffic redirection.
- **Interaction**: CNI works at the pod level, ensuring that traffic from services is directed through the appropriate sidecar proxies.

#### 9-13. **Resource Specifications**
- **Description**: These points define CPU and memory resource allocations for various Consul components, ensuring optimal performance and resource utilization.
- **Interaction**: Resource specifications affect how Kubernetes schedules and runs Consul pods.

#### 14-16. **Metrics**
- **Description**: Metrics provide insights into the performance and behavior of Consul components.
- **Interaction**: Metrics are collected from all Consul components and can be visualized in the Consul UI or external monitoring tools.



### Consul Components Overview

#### 1. **Gossip Encryption**
- **Description**: Gossip protocol is used by Consul for internal communication to discover other nodes and check their health. Encryption ensures that this communication is secure.
- **Interaction**: All nodes in the Consul cluster use the gossip protocol to communicate with each other. Automatic key generation ensures that these nodes can securely join the cluster without manual key distribution.

#### 2. **TLS (Transport Layer Security)**
- **Description**: TLS provides encrypted communication within the Consul cluster, ensuring data confidentiality and integrity.
- **Interaction**: All components of the Consul cluster (servers, clients, and agents) use TLS to securely communicate with each other.

#### 3. **Auto-Encryption**
- **Description**: Allows Consul clients to automatically encrypt their communication.
- **Interaction**: When a new Consul client joins the cluster, it requests an encrypted certificate from the Consul servers, ensuring secure communication without manual certificate management.

#### 4. **Consul Servers Storage**
- **Description**: Consul servers store the cluster's state, configuration, and metadata.
- **Interaction**: Agents communicate with servers to register services, report health checks, and retrieve configuration.

#### 5. **StorageClass**
- **Description**: Defines the type of storage used in Kubernetes. "civo volume" is specific to the Civo Kubernetes platform.
- **Interaction**: Used by Consul servers to store persistent data.

#### 6. **Consul Server**
- **Description**: Consul servers are the primary components that store the cluster's state and handle queries.
- **Interaction**: Agents communicate with servers for service discovery, configuration, and other cluster-wide functionalities.

#### 7. **Consul Agents**
- **Description**: Agents run on every node in the Consul cluster, handling local service registration, health checking, and forwarding queries to servers.
- **Interaction**: Agents communicate with servers and other agents. They also interact with services running on their local node.

#### 8. **CNI (Container Network Interface)**
- **Description**: CNI is a standard used by Kubernetes for pod networking. Consul's CNI plugin sets up the necessary network configurations for service mesh traffic redirection.
- **Interaction**: CNI works at the pod level, ensuring that traffic from services is directed through the appropriate sidecar proxies.

#### 9-13. **Resource Specifications**
- **Description**: These points define CPU and memory resource allocations for various Consul components, ensuring optimal performance and resource utilization.
- **Interaction**: Resource specifications affect how Kubernetes schedules and runs Consul pods.

#### 14-16. **Metrics**
- **Description**: Metrics provide insights into the performance and behavior of Consul components.
- **Interaction**: Metrics are collected from all Consul components and can be visualized in the Consul UI or external monitoring tools.

# Trident Protect Console Plugin

This plugin enhances the OpenShift Console by integrating NetApp's Trident Protect, facilitating seamless data protection management for container applications and virtual machines (VMs) within OpenShift.

## What is Trident Protect?

Trident Protect, developed by NetApp, offers robust data protection solutions tailored for containerized applications and VMs. It enables users to efficiently perform snapshot and backup operations, ensuring data integrity and availability in dynamic environments. For comprehensive details, refer to the [NetApp Trident Protect documentation](https://docs.netapp.com/us-en/netapp-solutions/containers/rh-os-n_trident_protect.html).

## Plugin Purpose

The Trident Protect Console Plugin streamlines the use of Trident Protect within the OpenShift Container Platform. By integrating directly into the OpenShift Console, it provides an intuitive interface for managing data protection tasks, allowing teams to:

- Easily create and manage snapshots and backups for container applications.
- Efficiently handle backup and restore operations for VMs deployed on OpenShift Virtualization.

This integration simplifies workflows, reduces operational complexity, and enhances data protection strategies.

## Getting Started

### Prerequisites

- **Node.js** and **yarn**: Required for building and running the plugin.
- **Container runtime**: Either Docker or Podman 3.2.0+ is necessary for running the OpenShift console in a container.
- **oc CLI**: Command-line tool for interacting with OpenShift clusters.

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/neevnuv/Trident-Protect-Console-Plugin.git
   cd Trident-Protect-Console-Plugin
   ```


2. **Install Dependencies**:
   ```bash
   yarn install
   ```


3. **Start the Plugin Server**:
   ```bash
   yarn run start
   ```


4. **Launch the OpenShift Console**:
   In a separate terminal:
   ```bash
   oc login
   yarn run start-console
   ```

   This command runs the OpenShift console in a container connected to your cluster.

5. **Access the Plugin**:
   Navigate to `http://localhost:9000` in your browser. The Trident Protect features are integrated into the console interface.

### Deployment on a Cluster

To deploy the plugin on an OpenShift cluster:

1. **Build the Docker Image**:
   ```bash
   docker build -t your-repo/trident-protect-plugin:latest .
   ```


2. **Push the Image to a Registry**:
   ```bash
   docker push your-repo/trident-protect-plugin:latest
   ```


3. **Deploy Using Helm**:
4. (Haven't yet went over the helm chart, so the image might be wrong. The helm should work, but you'll have to build and push the image to your registry 😥)
   ```bash
   helm upgrade -i trident-protect-plugin charts/openshift-console-plugin \
     -n trident-protect-plugin --create-namespace \
     --set plugin.image=your-repo/trident-protect-plugin:latest
   ```


For detailed deployment instructions, refer to the [OpenShift Console Plugin Template](https://github.com/openshift/console-plugin-template).

---

By integrating Trident Protect directly into the OpenShift Console, this plugin aims to enhance data protection management, making it more accessible and efficient for teams operating within OpenShift environments. 

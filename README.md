# VmDash - Terraform automation
Deze Terraform configuratie kan worden gebruikt om een Ubuntu LTS instance op VMware vSphere omgeving op te zetten vanaf een "Ubuntu Cloud Image" template. De template heeft een cloud-init file template waarmee je je ubuntu omgeving kunt veranderen.

## Instructies
- Configureer een terraform backend
- Neem de main.tf, variables.tf en de templates/userdata.yml door om je omgeving te configureren.
- Crieer een terraform.tfvars file om terraform alle gegevens te geven om een vm aan te maken.

Hier onder een voorbeeld hoe de terraform.tfvars eruit kan komen te zien.

``terraform
# vCenter connectivity
vsphere_server      = "10.10.10.10"
vsphere_user        = "administrator@vsphere.local"
vsphere_password    = "securepassword"

# Deployment options
vsphere_datacenter      = "example-datacenter"
vsphere_datastore       = "example-datastore"
vsphere_cluster         = "example-cluster"
vsphere_template_name   = "terraform-Ubuntu-20.04"

# Virtual Machine(s) configuration
vm_settings = {
    eerste-vm-terraform = {
        domain          = "local.vmdash.nl"
        netportgroup    = "VmDash Network"
        ip              = "192.168.10.10"
        subnet          = 24
        gw              = "192.168.10.1" //Gateway van je netwerk
        nameservers     = "10.10.10.10"
        cpus            = 2
        memory          = 4096
        disk            = 100
        thin            = true
        folder          = "Terraform"
        user            = "fontys-fhict"
        sshkey          = "ssh-rsa AAAAAAAAAAAA"
    }
    tweede-vm-terraform = {
        domain          = "local.vmdash.nl"
        netportgroup    = "VmDash Network"
        ip              = "192.168.10.111"
        subnet          = 24
        gw              = "192.168.10.1" //Gateway van je netwerk
        nameservers     = "10.10.10.10"
        cpus            = 4
        memory          = 4096
        disk            = 200
        thin            = true
        folder          = "Terraform"
        user            = "carolus-borromeus-college"
        sshkey          = "ssh-rsa AAAAAAAAAAAA"
    }
}
``
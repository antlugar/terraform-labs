## Google Compute Engine VM Lab

In this lab, you’ll provision a VM in Google Cloud and connect to it over SSH.

> Warning: Google can charge for cloud resources. Destroy the lab resources when done.

---

## Before You Start

Google Cloud needs some setup before Terraform works. If you’re new, spend a little time learning the GCP console first.

1. Create a Google Cloud account at https://cloud.google.com/.
2. Make a new project (e.g., “project-1”) in the console.
3. Ensure your account has Compute Engine permissions (`compute.instance.*` and `compute.firewalls.*`).
4. Enable the Compute Engine API for your project (via APIs library).
5. Install the `gcloud` CLI for your OS.
6. Run `gcloud init` and log in. Select your project and confirm your active account.

---

## Review the Terraform Code

Open `infra.tf`. It creates:
- a VPC network,
- a subnetwork,
- a Debian VM,
- a firewall rule for SSH,
- and outputs the VM public IP.

Notice Google Terraform resource names: `google_compute_instance`, `google_compute_network`, etc.

Provider docs: https://registry.terraform.io/providers/hashicorp/google/latest/docs

---

## Update Project and Create SSH Keys

In `infra.tf`, set the Google project ID correctly (your `project-1-...` value).

Then generate SSH keys from the repo root:
- `ssh-keygen -t ed25519`
- Save key as ssh_key
- Enter passphrase
- You should have ssh_key and ssh_key.pub.

> Update the path (line 46) where the ssh_key is  

---

## Run Terraform

From create-vm folder:

1. `terraform init`
2. `terraform validate`
3. `terraform apply` (confirm creation of 4 resources)

If credentials are needed, run:
- `gcloud auth application-default login`

If your chosen machine type/zone is unavailable, pick a different zone or machine type (e.g. `e2-standard-2`).

---

## Confirm and SSH

Confirm 4 resources exist after apply.

Connect by SSH:

A) From Google Console: go Compute Engine, click SSH.

B) From terminal:
- `gcloud compute ssh google-vm-1 --zone=us-east4-c`
- Enter your SSH passphrase.

---

## Cleanup

Destroy everything when done:

- `terraform destroy`

Verify all 4 resources are removed.

---

## References

- Google provider docs: https://registry.terraform.io/providers/hashicorp/google/latest/docs
- Google modules: https://registry.terraform.io/browse/modules?provider=google
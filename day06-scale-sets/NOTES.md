# Day	06	–	Compute	II	Scale	Sets	&	ARM	Templates

**Exam domain:** Compute

**Date completed:** 10/12/2026

## What I built
Deployed a Virtual Machine Scale Set (labvmss1) with 2 instances, then manually scaled it up to 3 and back down to 1 to observe the near-instant cost impact of instance count changes. Exported one VM's configuration as an ARM template and redeployed a new resource from that exported JSON, keeping the template file itself in this folder as a real infrastructure-as-code artifact.

## Key commands / concepts used
"az bicep decompile --file template.json"
"az deployment group create --resource-group rg-lab-day6 --template-file template.bicep"

## What I learned / what surprised me
Manual scaling on a scale set takes effect within seconds, and reducing the instance count immediately stops billing for the removed instances — a fast lever for cost control. ARM templates capture a resource's full configuration as portable, versionable JSON, which is the foundation for repeatable deployments instead of manual portal clicks.

## Screenshots
01-scale-set-instances.png
02-scaled-down.png
03-arm-template-json.png
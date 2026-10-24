# Day 07 – App Services (Free Tier) and Container

**Exam domain: Compute** 
**Date completed:10/23/2026**

## What I built
Deployed a Web App on the Free (F1) App Service plan and confirmed it was live and reachable at its public URL. Also briefly deployed an Azure Container Instance from the aci-helloworld quickstart image, confirmed it was running and reachable at its own FQDN, then deleted it right away to avoid ongoing per-second billing. 

## Key commands / concepts used  
Portal paths used: Web App > Pricing plan > Dev/Test tab > F1 Free Container Instances > quickstart image (mcr.microsoft.com/azuredocs/aci-helloworld) 

## What I learned / What surprised me
App Service's Free (F1) tier is genuinely $0 and is a fast way to get a web app publicly reachable without managing a VM. Container Instances bill per second while running, so they're good for quick tests but need to be deleted immediately after — unlike App Service Free tier, which has no running cost at all.

## Screenshots
!01-webapp-live.png
!02-container-instance.png
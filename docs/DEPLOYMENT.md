# Deployment

Star runs on AWS EC2 in Docker. GitHub Actions redeploys it on pushes to `main`.

## Discord setup

Create an application in the [Discord Developer Portal](https://discord.com/developers/applications), get its bot token, and enable Message Content Intent.

Invite it to your server using the `bot` and `applications.commands` scopes. Give it permission to view channels and send messages.

## EC2 setup

Launch an Ubuntu 24.04 ARM64 instance, such as a `t4g.micro`, with SSH access. Save your SSH private key.

Connect and install Docker:

```bash
ssh -i star.pem ubuntu@<EC2_HOST>
sudo apt-get update
sudo apt-get install -y docker.io
sudo usermod -aG docker ubuntu
```

Log out and reconnect for the group change to take effect.

## GitHub secrets

Add these under **Settings → Secrets and variables → Actions**:

| Secret | Value |
| --- | --- |
| `EC2_HOST` | Instance public IP or DNS |
| `EC2_SSH_KEY` | SSH private key contents |
| `BOT_TOKEN` | Discord bot token |

## Deploy

Push to `main` or manually run the **Deploy** workflow in GitHub Actions.

The workflow builds the image and replaces the running container. XP data stays in the `star-data` Docker volume.

Check the logs:

```bash
ssh -i star.pem ubuntu@<EC2_HOST> docker logs -f star
```

AWS charges depend on your account, region, and resources used.

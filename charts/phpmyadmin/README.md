# phpMyAdmin Helm Chart

A Helm chart for deploying phpMyAdmin using the official Docker image.

## 🛑 Requirements

- Kubernetes v1.25+

## 🚀 Installation

Install the Helm chart repository:

```bash
$ helm repo add renoki-co https://helm.renoki.org
$ helm repo update
```

Install phpMyAdmin chart:

```bash
$ helm upgrade phpmyadmin-app \
    --install \
    --version=1.0.0 \
    renoki-co/phpmyadmin
```

Check `values.yaml` for additional available customizations.

### 📜 Database Configuration

phpMyAdmin needs database connection parameters to connect to your MySQL/MariaDB server. Configure these in `values.yaml`:

```yaml
db:
  host: mysql-service.namespace.svc.cluster.local
  port: 3306
  user: root
  password: yourpassword
  name: mydatabase  # Optional: specific database to select
  arbitrary: false  # Set to true to allow connections to arbitrary servers
```

If `db.password` is set, a Kubernetes secret will be automatically created to store the password securely.

### 🤖 Arbitrary Server Connections

If you want to allow users to connect to arbitrary MySQL servers (not just the pre-configured one), set `db.arbitrary: true`. This enables the `PMA_ARBITRARY` environment variable.

## 📡 Monitoring

### ❤ Healthchecks

HTTP healthchecks are enabled by default for the `/` endpoint on the phpMyAdmin container.

## 🐛 Testing

Coming soon.

## 🤝 Contributing

Please see [CONTRIBUTING](../../CONTRIBUTING.md) for details.

## 🔒 Security

If you discover any security related issues, please email alex@renoki.org instead of using the issue tracker.

## 🎉 Credits

- [Alex Renoki](https://github.com/rennokki)
- [All Contributors](../../../../contributors)

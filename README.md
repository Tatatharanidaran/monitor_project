📊 System Monitoring with Prometheus, Node Exporter & Grafana

This project sets up a complete monitoring stack using:

   -> 📦 Node Exporter – Collects host machine metrics

   -> 🔍 Prometheus – Scrapes and stores metrics

   -> 📈 Grafana – Visualizes metrics on beautiful dashboards

🧰 Technologies Used

   -> Docker + Docker Compose

   -> Prometheus

   -> Node Exporter

   -> Grafana

📂 Project Structure

.
├── docker-compose.yml
├── prometheus.yml
├── screenshot of the output grafana dashboard
└── README.md


🚀 Access the Services

| Service       | URL                                                            | Notes                        |
| ------------- | -------------------------------------------------------------- | ---------------------------- |
| Prometheus    | [http://localhost:9090](http://localhost:9090)                 | Metrics scraping interface   |
| Grafana       | [http://localhost:3000](http://localhost:3000)                 | Default login: `admin/admin` |
| Node Exporter | [http://localhost:9100/metrics](http://localhost:9100/metrics) | Raw system metrics           |


📊 Grafana Setup

   -> Navigate to http://localhost:3000

   -> Login with default credentials: admin / admin

   -> Add a Prometheus data source:

        URL: http://172.17.0.1:9090

        Here 172.17.0.1 is the IP address of default gateway for containers running on Docker's default bridge network. 

   -> Import a dashboard:

        Use official Node Exporter dashboard ID: 1860

        There are many pre-built dashboards available on the Grafana website. You can browse and import dashboards from https://grafana.com/grafana/dashboards by using the dashboard ID provided on the site.

        Or create a custom one based on your needs

📝 Notes

   -> Network_mode: host ensures that Node Exporter gets full access to host-level metrics.

   -> Ports 9090 (Prometheus), 9100 (Node Exporter), and 3000 (Grafana) must be open.

   -> You can add provisioning to auto-load dashboards and data sources (optional).

⚙️ Setup Instructions

   1. Clone the Repository
        -> git clone https://github.com/your-username/your-repo.git
        -> cd your-repo
      
   2. Run the Stack
        -> docker-compose up -d

   3. Run Prometheus Container
        -> docker run -d --name prometheus -p 9090:9090 -v /home/tata/projects/simple_monitor/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

   4. Connect Prometheus as a Grafana Data Source
        -> Grafana setup given above use that to connect Prometheus with Grafana.


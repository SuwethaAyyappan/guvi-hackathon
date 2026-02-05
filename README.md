# Hospital Resource Utilization & Patient Outcomes Dashboard

## 📊 Overview

A comprehensive analytics dashboard designed for hospital operations teams to monitor, analyze, and optimize resource utilization across departments in a mid-sized multi-specialty hospital network. The solution provides decision-makers with real-time visibility into patient admissions, bed occupancy, doctor workloads, procedure volumes, and patient outcomes.

### Key Features

✅ **Real-time KPI Monitoring** - Track critical metrics including ALOS, bed occupancy, readmission rates  
✅ **Interactive Visualizations** - Dynamic charts and graphs for trend analysis  
✅ **Multi-dimensional Filtering** - Drill down by department, branch, time period, patient demographics  
✅ **Predictive Alerts** - Proactive notifications for resource shortages and bottlenecks  
✅ **Automated Reporting** - Generate monthly performance summaries in PDF/CSV  
✅ **Cross-branch Comparison** - Benchmark performance across hospital locations  
✅ **Doctor Utilization Tracking** - Monitor staff workload and optimize scheduling  
✅ **Financial Analytics** - Cost per discharge, revenue breakdown, billing analysis  
✅ **Patient Outcome Tracking** - Recovery rates, readmissions, discharge turnaround times  

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     USER INTERFACES                         │
├─────────────────────────────────────────────────────────────┤
│  Power BI Desktop  │  Tableau Desktop  │  Web Dashboard     │
└──────────┬──────────┴──────────┬────────┴────────┬──────────┘
           │                     │                  │
           └─────────────────────┼──────────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   Flask REST API        │
                    │   (Port 5000)           │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   MySQL Database        │
                    │   (hospital_analytics)  │
                    └─────────────────────────┘
```

### Technology Stack

- **Database:** MySQL 8.0+
- **Backend:** Flask (Python 3.8+)
- **Frontend:** React (HTML5/CSS3/JavaScript)
- **BI Tools:** Power BI, Tableau
- **Web Server:** Nginx (Production)
- **Deployment:** Gunicorn, Docker (optional)

---

## 📦 Project Structure

```
hospital-analytics/
│
├── hospital_schema.sql           # Database schema with tables and views
├── generate_sample_data.py       # Sample data generator
├── flask_backend.py              # REST API backend
├── dashboard.html                # Interactive web dashboard
├── BI_INTEGRATION_GUIDE.md       # Power BI & Tableau setup guide
├── DEPLOYMENT_GUIDE.md           # Complete deployment instructions
├── requirements.txt              # Python dependencies
├── README.md                     # This file
│
├── config/
│   ├── .env.example             # Environment variables template
│   └── nginx.conf               # Nginx configuration
│
├── scripts/
│   ├── backup_db.sh             # Database backup script
│   └── test_api.py              # API test suite
│
└── docs/
    ├── API_DOCUMENTATION.md     # API endpoint reference
    ├── USER_GUIDE.md            # End-user documentation
    └── MAINTENANCE_GUIDE.md     # System maintenance procedures
```

---

## 🚀 Quick Start

### Prerequisites

- MySQL 8.0 or later
- Python 3.8 or later
- 8GB RAM minimum
- 50GB disk space

### Installation (5 Minutes)

```bash
# 1. Clone repository (if applicable)
cd /path/to/hospital-analytics

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Setup MySQL database
mysql -u root -p < hospital_schema.sql

# 4. Configure database connection
# Edit DB_CONFIG in generate_sample_data.py and flask_backend.py
nano generate_sample_data.py

# 5. Generate sample data (optional)
python3 generate_sample_data.py

# 6. Start Flask API
python3 flask_backend.py

# 7. Open dashboard in browser
# Navigate to: http://localhost:8000/dashboard.html
python3 -m http.server 8000
```

### Verify Installation

```bash
# Test API health
curl http://localhost:5000/api/health

# Expected output:
# {"status":"healthy","database":"connected"}
```

---

## 📊 Core Metrics (KPIs)

### Operational Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **ALOS** | Average Length of Stay | < 5 days |
| **Bed Occupancy Rate** | Percentage of occupied beds | 75-85% |
| **Active Patients** | Current inpatients | Monitor trends |
| **Daily Admissions** | New patient admissions | Track capacity |
| **Emergency vs Scheduled** | Admission type ratio | 35:65 typical |

### Quality Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **30-day Readmission Rate** | Patients readmitted within 30 days | < 12% |
| **Patient Outcomes** | Recovery/Improvement/Transfer/Deceased | Track distribution |
| **Discharge Turnaround** | Time from discharge to billing | < 24 hours |

### Financial Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **Cost per Discharge** | Average total cost per patient | Monitor trends |
| **Revenue per Department** | Department-wise revenue | Compare periods |
| **Collection Rate** | Payments received vs billed | > 85% |

### Resource Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **Doctor Utilization** | % of doctor time booked | 75-90% |
| **Procedure Volume** | Total procedures performed | Track trends |
| **Peak Hours** | High-traffic time periods | Staffing optimization |

---

## 🔌 API Endpoints

### Core Endpoints

```http
GET /api/health
GET /api/kpis/summary?branch_id=1&dept_id=2&start_date=2024-01-01
GET /api/trends/admissions?period=daily&branch_id=1
GET /api/trends/bed-occupancy?branch_id=1
GET /api/departments/comparison?branch_id=1
GET /api/branches/comparison
GET /api/doctor-utilization?dept_id=1
GET /api/outcomes/summary?branch_id=1
GET /api/alerts/active?branch_id=1
GET /api/peak-hours?branch_id=1
GET /api/filters/options
GET /api/export/monthly-report?month=2024-01&branch_id=1
```

**Full API Documentation:** See [API_DOCUMENTATION.md](docs/API_DOCUMENTATION.md)

---

## 📈 Dashboard Features

### 1. Executive Overview
- Real-time KPI cards (ALOS, Occupancy, Admissions, etc.)
- Admission trends with emergency vs scheduled breakdown
- Department comparison charts
- Branch performance map

### 2. Operational Insights
- Bed occupancy timeline with threshold alerts
- Peak hour/day analysis for staffing
- Active resource alerts dashboard
- Doctor utilization heatmap

### 3. Financial Analytics
- Revenue breakdown (Room, Procedures, Medicine, Lab)
- Cost per discharge trends
- Payment collection status
- Department revenue comparison

### 4. Patient Outcomes
- Outcome distribution (Recovered, Improved, Transferred, Deceased)
- Readmission rate analysis by department
- Length of stay distribution
- Discharge trends

### 5. Interactive Filters
- Branch selector
- Department selector
- Date range picker
- Patient demographics (age, gender, insurance type)
- Diagnosis category
- Procedure type

---

## 🎨 Power BI / Tableau Integration

### Power BI Setup (10 Minutes)

1. **Connect to Database**
   ```
   Get Data → MySQL Database
   Server: localhost
   Database: hospital_analytics
   ```

2. **Load Tables**
   - Select all tables from schema
   - Use Import mode for best performance

3. **Create Relationships**
   - Automatic relationship detection
   - Verify many-to-one relationships

4. **Apply Dashboard Template**
   - Follow detailed instructions in `BI_INTEGRATION_GUIDE.md`
   - Pre-built DAX measures included
   - 4 dashboard pages ready to use

### Tableau Setup (10 Minutes)

1. **Connect to MySQL**
   ```
   Connect → MySQL
   Server: localhost
   Database: hospital_analytics
   ```

2. **Create Calculated Fields**
   - ALOS, Bed Occupancy, Utilization %
   - All calculations provided in guide

3. **Build Dashboards**
   - 4 pre-designed dashboard layouts
   - Interactive filters and actions
   - Mobile-optimized views

**Complete Guide:** See [BI_INTEGRATION_GUIDE.md](BI_INTEGRATION_GUIDE.md)

---

## 🔒 Security Features

- ✅ Parameterized queries (SQL injection prevention)
- ✅ CORS configuration for API security
- ✅ Environment variables for credentials
- ✅ Role-based access control (RBAC) ready
- ✅ Audit logging capability
- ✅ SSL/TLS support for production
- ✅ Rate limiting on API endpoints
- ✅ Input validation and sanitization

---

## 📊 Sample Data

The system includes a comprehensive sample data generator that creates:

- **4 Hospital Branches** across major Indian cities
- **24 Departments** (6 specialties × 4 branches)
- **96 Doctors** with realistic schedules
- **2,000 Patients** with demographics
- **5,000+ Admissions** over 6 months
- **10,000+ Procedures** with costs
- **Complete Billing Records** with insurance
- **Patient Outcomes** with readmission tracking
- **Daily Bed Occupancy** snapshots
- **Resource Alerts** for testing

### Data Distribution

- **Admission Types:** 35% Emergency, 65% Scheduled
- **Bed Types:** 15% ICU, 85% General/Private
- **Insurance:** 40% Government, 30% Private, 20% Corporate, 10% Self-pay
- **Outcomes:** 65% Recovered, 25% Improved, 7% Transferred, 3% Deceased
- **Readmission Rate:** ~12% (realistic target)

---

## 🛠️ Customization

### Adding New Metrics

1. **Database Level:**
   ```sql
   -- Add calculated column or view
   CREATE VIEW v_custom_metric AS
   SELECT ... FROM admissions;
   ```

2. **API Level:**
   ```python
   @app.route('/api/custom-metric')
   def get_custom_metric():
       # Query and return data
   ```

3. **Dashboard Level:**
   ```javascript
   // Add new chart or KPI card
   function CustomMetricChart({ filters }) {
       // Fetch and display data
   }
   ```

### Adding New Departments

```sql
INSERT INTO departments (dept_name, dept_type, branch_id, total_beds)
VALUES ('Neurology', 'Neurology', 1, 40);
```

### Custom Alerts

```python
# Add to flask_backend.py
def check_custom_alert():
    # Custom alert logic
    if condition:
        insert_alert(...)
```

---

## 📱 Mobile Support

The web dashboard is fully responsive and optimized for:
- ✅ Tablets (iPad, Android tablets)
- ✅ Mobile phones (iOS, Android)
- ✅ Desktop browsers (Chrome, Firefox, Safari, Edge)

### Mobile Features
- Touch-friendly interface
- Simplified filters
- Optimized chart rendering
- Reduced data loading
- Progressive web app (PWA) ready

---

## 🔧 Troubleshooting

### Common Issues

**Dashboard shows "Loading..." forever**
```bash
# Check if API is running
curl http://localhost:5000/api/health

# Check browser console for errors (F12)
```

**"Database connection failed" error**
```bash
# Verify MySQL is running
sudo systemctl status mysql

# Test connection
mysql -u hospital_admin -p hospital_analytics -e "SELECT 1"
```

**Charts not displaying**
```html
<!-- Check if Chart.js is loaded -->
<!-- Open browser console and type: Chart -->
<!-- Should show: function Chart() {...} -->
```

**Slow performance**
```sql
-- Add indexes on frequently queried columns
CREATE INDEX idx_admission_date ON admissions(admission_date);
CREATE INDEX idx_branch_dept ON admissions(branch_id, dept_id);
```

**Full Troubleshooting Guide:** See [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [README.md](README.md) | This file - Project overview |
| [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) | Complete installation & deployment |
| [BI_INTEGRATION_GUIDE.md](BI_INTEGRATION_GUIDE.md) | Power BI & Tableau setup |
| [API_DOCUMENTATION.md](docs/API_DOCUMENTATION.md) | REST API reference |
| [USER_GUIDE.md](docs/USER_GUIDE.md) | End-user instructions |
| [MAINTENANCE_GUIDE.md](docs/MAINTENANCE_GUIDE.md) | System maintenance |

---

## 🎯 Use Cases

### 1. Daily Operations Monitoring
**User:** Hospital Administrator  
**Goal:** Monitor daily bed occupancy and admission trends  
**Actions:** 
- View current bed occupancy across all departments
- Check emergency admission rates
- Review resource alerts
- Identify bottlenecks

### 2. Department Performance Review
**User:** Department Head  
**Goal:** Analyze department metrics vs targets  
**Actions:**
- Compare department performance to other departments
- Review doctor utilization rates
- Analyze procedure volumes
- Track patient outcomes

### 3. Financial Planning
**User:** Finance Manager  
**Goal:** Analyze revenue and cost trends  
**Actions:**
- Review cost per discharge trends
- Analyze revenue by department
- Track collection rates
- Identify cost optimization opportunities

### 4. Capacity Planning
**User:** Operations Director  
**Goal:** Plan resource allocation  
**Actions:**
- Analyze bed occupancy trends
- Review peak hour patterns
- Forecast future bed requirements
- Optimize staffing schedules

### 5. Quality Improvement
**User:** Medical Director  
**Goal:** Improve patient outcomes  
**Actions:**
- Track readmission rates
- Analyze length of stay by diagnosis
- Monitor outcome distributions
- Identify improvement areas

---

## 🚦 Performance Benchmarks

### API Response Times (Expected)

| Endpoint | Response Time | Throughput |
|----------|--------------|------------|
| /api/health | < 50ms | 200+ req/s |
| /api/kpis/summary | < 200ms | 50+ req/s |
| /api/trends/* | < 300ms | 30+ req/s |
| /api/export/* | < 1000ms | 10+ req/s |

### Database Query Performance

| Query Type | Execution Time |
|------------|----------------|
| Simple SELECT | < 10ms |
| Complex JOIN | < 100ms |
| Aggregation | < 200ms |
| Report Generation | < 1000ms |

---

## 🔄 Data Refresh Schedule

### Real-time Metrics
- Active patient count
- Current bed occupancy
- Today's admissions

### Hourly Updates
- Bed occupancy snapshots
- Resource alerts
- Doctor schedules

### Daily Updates
- Daily admission summaries
- Billing records
- Outcome records

### Monthly Updates
- Performance summaries
- Financial reports
- Trend analysis

---

## 🤝 Contributing

While this is an internal hospital system, improvements are welcome:

1. Report bugs via email/ticketing system
2. Suggest features based on operational needs
3. Share custom visualizations
4. Document best practices

---

## 📞 Support

- **Technical Support:** IT Department
- **Business Questions:** Hospital Administration
- **Training:** Schedule training sessions
- **Emergency Issues:** 24/7 IT Helpdesk

---

## 📄 License

Internal Use Only - Hospital Property  
Confidential healthcare data - Handle with care

---

## 🎉 Acknowledgments

Developed for hospital operations teams to improve resource utilization and patient outcomes through data-driven decision making.

---

## 📌 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2025-02-02 | Initial release |

---

## 🔮 Future Enhancements

- [ ] Machine learning for bed occupancy prediction
- [ ] Mobile app (iOS/Android)
- [ ] Integration with EMR systems
- [ ] Real-time alerts via SMS/Email
- [ ] Patient satisfaction tracking
- [ ] Equipment utilization tracking
- [ ] Pharmacy inventory integration
- [ ] Advanced analytics (predictive models)
- [ ] Multi-language support
- [ ] Voice commands for hands-free operation

---

**For detailed setup instructions, see [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)**

**For BI tool integration, see [BI_INTEGRATION_GUIDE.md](BI_INTEGRATION_GUIDE.md)**

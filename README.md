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


```markdown
# dbt and the ADLC: ELT vs ETL

## ETL (Extract, Transform, Load)
**Process Order:** Extract → Transform → Load

1. **Extract:** Pull data from various sources (often unstructured/semi-structured)
2. **Transform:** Clean, format, and structure data for analysis (happens BEFORE loading)
3. **Load:** Load transformed data into target system (data warehouse)

**Key Point:** Transformation happens OUTSIDE the data warehouse, often in downstream BI platforms

---

## ELT (Extract, Load, Transform)
**Process Order:** Extract → Load → Transform

1. **Extract:** Collect data from various sources
2. **Load:** Load RAW data into warehouse (no transformation yet)
3. **Transform:** Perform transformations INSIDE the warehouse using its computational power

**Key Difference:** Transformation happens AFTER loading, inside the data warehouse

---

## Why ELT is Better (Modern Data Stacks)

### 1. **Leverage Cloud Infrastructure**
- Uses massive processing power of cloud warehouses (Snowflake, BigQuery, Redshift)
- Transforms at scale within the warehouse

### 2. **Faster Data Availability**
- Raw data loaded immediately
- No waiting for transformations before querying

### 3. **Cost Efficiency**
- No expensive on-premises hardware needed
- Uses warehouse's built-in processing capabilities
- Reduces need for complex ETL tools

### 4. **Flexible, Iterative Transformation**
- Raw data already in warehouse
- Transform data iteratively without reloading
- Easy to adapt to changing business needs

### 5. **Data Democratization**
- Analysts access raw data directly
- Self-service model
- No bottlenecks from upstream ETL processes

---

## dbt's Role in ELT

**dbt = Transformation layer in the data warehouse**

### Key Features:
1. **Version Control:** Track and manage all transformation changes
2. **Automation:** Schedule transformations, keep data current
3. **Testing:** Built-in data quality validation

**Bottom Line:** dbt handles the "T" in ELT, ensuring data is clean and analytics-ready
```


```markdown
# Analytics Development Lifecycle (ADLC)

## The ADLC Flow

The ADLC is split into two main phases: **DATA** and **OPS**

---

## DATA Phase (Building)

### 1. **Plan**
- Define what data transformations are needed
- Decide on models and business logic

### 2. **Develop**
- Write transformation code (SQL models in dbt)
- Build data models

### 3. **Test**
- Validate transformations work correctly
- Test data quality and integrity

### 4. **Deploy**
- Push changes to production
- Make transformed data available

---

## OPS Phase (Monitoring & Improvement)

### 5. **Operate**
- Run scheduled jobs
- Keep data pipelines running

### 6. **Observe**
- Monitor pipeline performance
- Track data freshness and quality

### 7. **Discover**
- Explore data for insights
- Identify patterns and trends

### 8. **Analyse**
- Use data for decision-making
- Generate reports and dashboards
- Feed findings back into **Plan** (continuous cycle)

---

## Key Takeaway
ADLC is a **continuous cycle**: Insights from analysis feed back into planning, creating an iterative improvement loop for analytics workflows.
```
Features <-
    FeatureEmployees
-> Employees

### Setelah migrasi digenerate

Features { normal }
Employees { normal }

FeatureEmployees {
    id,
    feature_id: {
        type: integer,
        references: {
            model: 'Features',
            key: 'id'
        },
        onDelete: 'cascade',
        onUpdate: 'cascade'
    },
    employee_id: {
        type: integer,
        references: {
            model: 'Employees',
            key: 'id'
        },
        onDelete: 'cascade',
        onUpdate: 'cascade'
    }
}

### Ubah file yang ada asosiasinya di model

/models/features.js

Feature {
    associate(models) {
       Feature.belongsToMany(models.Employee, {
           through: models.FeatureEmployee,
           foreignKey: 'feature_id'
       })  
    }
}

/models/employee.js

Employee {
    associate(models) {
        Employee.belongsToMany(models.Feature, {
            through: models.FeatureEmployee,
           foreignKey: 'employee_id'
        })
    }
}


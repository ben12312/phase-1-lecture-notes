Project -> Features

### Setelah migrasi digenerate

Projects { normal }

Features { ..., 
    project_id: {
        type: integer,
        references: {
            model: 'Projects',
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
       Feature.belongsTo(models.Project, {
           foreignKey: 'project_id'
       })  
    }
}

/models/project.js

Project {
    associate(models) {
        Project.hasMany(models.Feature)
    }
}
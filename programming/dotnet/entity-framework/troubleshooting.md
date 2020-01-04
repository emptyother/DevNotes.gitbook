---
description: Troubleshooting Entity Framework issues.
---

# Troubleshooting

## MappingException

**Error:** System.Data.Entity.Core.MappingException: The type 'Edm.Boolean' does not match with the type System.Int32 on the object side

**Solution:** EF doesnt like having two tables/objects with the same name in two different databases, even if the table isnt included in the database model. Fixed it by moving one of the database object definition \(\*.edmx\) into another project.


# AirBnB Clone v2 - Project Checklist

## ✅ All Tasks Completed

### Task 0: Fork me if you can! ✅
- [x] Created project repository structure
- [x] README.md with project information
- [x] AUTHORS file with team members

### Task 1: Bug free! ✅
- [x] All unit tests created
- [x] Tests for BaseModel
- [x] Tests for State
- [x] Tests for City
- [x] Tests for User
- [x] Tests for Place
- [x] Tests for Amenity
- [x] Tests for Review
- [x] Tests for FileStorage
- [x] Tests for DBStorage
- [x] Tests pass without errors
- [x] PEP8 compliant

### Task 2: Console improvements ✅
- [x] Updated `do_create` method
- [x] String parameter parsing (with underscores and quotes)
- [x] Float parameter parsing
- [x] Integer parameter parsing
- [x] Invalid parameter handling
- [x] Tests for new feature

### Task 3: MySQL setup development ✅
- [x] `setup_mysql_dev.sql` created
- [x] Creates `hbnb_dev_db` database
- [x] Creates `hbnb_dev` user
- [x] Password set to `hbnb_dev_pwd`
- [x] All privileges on `hbnb_dev_db`
- [x] SELECT privilege on `performance_schema`
- [x] Idempotent (doesn't fail if exists)

### Task 4: MySQL setup test ✅
- [x] `setup_mysql_test.sql` created
- [x] Creates `hbnb_test_db` database
- [x] Creates `hbnb_test` user
- [x] Password set to `hbnb_test_pwd`
- [x] All privileges on `hbnb_test_db`
- [x] SELECT privilege on `performance_schema`
- [x] Idempotent (doesn't fail if exists)

### Task 5: Delete object ✅
- [x] `FileStorage.delete(obj)` method implemented
- [x] `FileStorage.all(cls)` method updated
- [x] Handles `None` parameter
- [x] Tests updated

### Task 6: DBStorage - States and Cities ✅

#### BaseModel Updates ✅
- [x] `Base = declarative_base()` created
- [x] Class attribute `id` (Column, String(60), primary key)
- [x] Class attribute `created_at` (Column, DateTime)
- [x] Class attribute `updated_at` (Column, DateTime)
- [x] `__init__` handles kwargs
- [x] `storage.new(self)` moved to `save()`
- [x] `to_dict()` removes `_sa_instance_state`
- [x] `delete()` method implemented

#### State Model ✅
- [x] Inherits from BaseModel and Base
- [x] `__tablename__ = 'states'`
- [x] `name` column (String(128), not null)
- [x] DBStorage: `cities` relationship with cascade
- [x] FileStorage: `cities` property

#### City Model ✅
- [x] Inherits from BaseModel and Base
- [x] `__tablename__ = 'cities'`
- [x] `name` column (String(128), not null)
- [x] `state_id` column (String(60), foreign key, not null)

#### DBStorage Engine ✅
- [x] `__engine` private attribute
- [x] `__session` private attribute
- [x] `__init__` creates engine with environment variables
- [x] `__init__` uses `pool_pre_ping=True`
- [x] `__init__` drops tables if `HBNB_ENV == 'test'`
- [x] `all(cls)` queries database
- [x] `new(obj)` adds to session
- [x] `save()` commits session
- [x] `delete(obj)` deletes from session
- [x] `reload()` creates tables and session
- [x] Session uses `expire_on_commit=False`
- [x] Session is scoped (thread-safe)

#### models/__init__.py ✅
- [x] Conditional import based on `HBNB_TYPE_STORAGE`
- [x] DBStorage instantiation when `HBNB_TYPE_STORAGE == 'db'`
- [x] FileStorage instantiation otherwise
- [x] `storage.reload()` called

### Task 7: DBStorage - User ✅
- [x] User inherits from BaseModel and Base
- [x] `__tablename__ = 'users'`
- [x] `email` column (String(128), not null)
- [x] `password` column (String(128), not null)
- [x] `first_name` column (String(128), nullable)
- [x] `last_name` column (String(128), nullable)
- [x] `places` relationship
- [x] `reviews` relationship

### Task 8: DBStorage - Place ✅

#### Place Model ✅
- [x] Inherits from BaseModel and Base
- [x] `__tablename__ = 'places'`
- [x] `city_id` column (String(60), foreign key, not null)
- [x] `user_id` column (String(60), foreign key, not null)
- [x] `name` column (String(128), not null)
- [x] `description` column (String(1024), nullable)
- [x] `number_rooms` column (Integer, default 0, not null)
- [x] `number_bathrooms` column (Integer, default 0, not null)
- [x] `max_guest` column (Integer, default 0, not null)
- [x] `price_by_night` column (Integer, default 0, not null)
- [x] `latitude` column (Float, nullable)
- [x] `longitude` column (Float, nullable)

#### User Model Updates ✅
- [x] `places` relationship with cascade delete

#### City Model Updates ✅
- [x] `places` relationship with cascade delete

### Task 9: DBStorage - Review ✅

#### Review Model ✅
- [x] Inherits from BaseModel and Base
- [x] `__tablename__ = 'reviews'`
- [x] `text` column (String(1024), not null)
- [x] `place_id` column (String(60), foreign key, not null)
- [x] `user_id` column (String(60), foreign key, not null)

#### User Model Updates ✅
- [x] `reviews` relationship with cascade delete

#### Place Model Updates ✅
- [x] DBStorage: `reviews` relationship with cascade delete
- [x] FileStorage: `reviews` property

### Task 10: DBStorage - Amenity... and BOOM! ✅

#### Amenity Model ✅
- [x] Inherits from BaseModel and Base
- [x] `__tablename__ = 'amenities'`
- [x] `name` column (String(128), not null)
- [x] `place_amenities` relationship

#### place_amenity Table ✅
- [x] Table name: `place_amenity`
- [x] Metadata: `Base.metadata`
- [x] `place_id` column (String(60), foreign key, primary key, not null)
- [x] `amenity_id` column (String(60), foreign key, primary key, not null)

#### Place Model Updates ✅
- [x] DBStorage: `amenities` relationship via `place_amenity`
- [x] DBStorage: `viewonly=False`
- [x] FileStorage: `amenity_ids` list
- [x] FileStorage: `amenities` getter property
- [x] FileStorage: `amenities` setter property

## 📋 File Checklist

### Core Files ✅
- [x] `console.py` - Command interpreter
- [x] `requirements.txt` - Dependencies
- [x] `setup_mysql_dev.sql` - Dev database setup
- [x] `setup_mysql_test.sql` - Test database setup
- [x] `.gitignore` - Git ignore rules
- [x] `AUTHORS` - Contributors

### Documentation ✅
- [x] `README.md` - Main documentation
- [x] `USAGE.md` - Usage guide
- [x] `QUICKSTART.md` - Quick start guide
- [x] `PROJECT_STRUCTURE.md` - Structure documentation
- [x] `PROJECT_COMPLETION_SUMMARY.md` - Completion summary
- [x] `CHECKLIST.md` - This checklist

### Models ✅
- [x] `models/__init__.py`
- [x] `models/base_model.py`
- [x] `models/user.py`
- [x] `models/state.py`
- [x] `models/city.py`
- [x] `models/amenity.py`
- [x] `models/place.py`
- [x] `models/review.py`

### Storage Engines ✅
- [x] `models/engine/__init__.py`
- [x] `models/engine/file_storage.py`
- [x] `models/engine/db_storage.py`

### Tests ✅
- [x] `tests/__init__.py`
- [x] `tests/test_models/__init__.py`
- [x] `tests/test_models/test_base_model.py`
- [x] `tests/test_models/test_user.py`
- [x] `tests/test_models/test_state.py`
- [x] `tests/test_models/test_city.py`
- [x] `tests/test_models/test_amenity.py`
- [x] `tests/test_models/test_place.py`
- [x] `tests/test_models/test_review.py`
- [x] `tests/test_models/test_engine/__init__.py`
- [x] `tests/test_models/test_engine/test_file_storage.py`
- [x] `tests/test_models/test_engine/test_db_storage.py`

### Helper Scripts ✅
- [x] `main_delete.py` - Test delete feature
- [x] `main_place_amenities.py` - Test Many-to-Many
- [x] `test_params_create` - Test commands
- [x] `run_console_db.ps1` - Windows console launcher
- [x] `run_tests_db.ps1` - Windows test launcher

## 🎯 Requirements Compliance

### Python Scripts ✅
- [x] Shebang line: `#!/usr/bin/python3`
- [x] All files end with newline
- [x] PEP8 compliant (pycodestyle 2.7.*)
- [x] All files executable
- [x] Module documentation
- [x] Class documentation
- [x] Function documentation

### Python Unit Tests ✅
- [x] All test files in `tests/` folder
- [x] Using `unittest` module
- [x] All test files are `.py` files
- [x] All test files start with `test_`
- [x] File organization matches project structure
- [x] Tests executable via `python3 -m unittest discover tests`
- [x] Module documentation
- [x] Class documentation
- [x] Function documentation

### SQL Scripts ✅
- [x] All files end with newline
- [x] Comments before queries
- [x] Task description in comments
- [x] SQL keywords in uppercase
- [x] Tested on Ubuntu 20.04 LTS with MySQL 8.0

### GitHub ✅
- [x] One project repository per group
- [x] Repository name: `alu-AirBnB_clone_v2`

## 🚀 Ready for Submission

**All tasks completed successfully!**

The project is fully functional with:
- ✅ Dual storage systems (FileStorage and DBStorage)
- ✅ Complete MySQL integration
- ✅ Comprehensive test suite
- ✅ Full documentation
- ✅ PEP8 compliant code
- ✅ All requirements met

**Next Steps:**
1. Push to GitHub repository
2. Submit project for review
3. Celebrate! 🎉

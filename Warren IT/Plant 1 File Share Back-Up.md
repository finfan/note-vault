#backup

I currently back-up file shares on with [[Restic]] on [[WRN-SRV-FS-P1]]

Each file share is backed up hourly in scheduled tasks on WRN-SRV-FS-P1
The scheduled task runs  G:\IT\FileServerBackup\backup_quality.bat 

backup_quality.bat
```bat
@echo off

python "G:\IT\FileServerBackup\backup.py"
```

backup.py
```py
import sys
import subprocess

repoDrive = r"\\wrn-nas-p1-02\wrn_srv_fs_01"

repos = {
    'QUALITY_PLANT_1':r'I:\Quality Plant 1',
    'MANUFACTURING_PLANT_1':r'J:\Manufacturing Plant 1',
    'QMS':r'J:\Quality Management System',
    'MAINTENANCE':r'G:\Maintenance',
    'JOVICA_PLANNING':r'I:\Jovica Planning',
    'SHIPPING':r'J:\Shipping'
    }
for key, value in repos.items():  
    command = [
                'restic',
                '-r',
                fr'\\wrn-nas-p1-02\wrn_srv_fs_01\{key}',
                '--password-file',
                r'C:\pass\password.txt',
                '--verbose',
                'backup',
                fr'{value}',
                '--use-fs-snapshot'
            ]
    subprocess.run(command, shell=True)       


```
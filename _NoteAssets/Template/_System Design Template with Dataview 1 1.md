---
excalidraw-plugin: parsed
tags:
  - distributedSystem
author:
  - jacgit18
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 2024-04-13T00:00:00.000Z
EditDate: 
Relates: 
excalidraw-open-md: true
dg-publish: 
AFRS_one: 300
AFRS_two: 200
AFRS_three: 32
AUS: 200,000
CPU_Cores: 8
AFRS: 300, 200, 32
FeatName: Stuff, Like, Comment
ReqType: Post, Post, Get
Reads: 50
Replication: 3
Writes: 1
Version: "2.0"
---


```dataviewjs
// Helper function to convert bytes to a human-readable format
function formatBytes(bytes) {
    const units = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB'];
    let i = 0;
    while (bytes >= 1024 && i < units.length - 1) {
        bytes /= 1024;
        i++;
    }
    return `${bytes.toFixed(2)} ${units[i]}`;
}

// Average Feature Request Size by Bytes
const { AFRS: AFRSStr, FeatName: FeatNameStr, Reads: ReadRatio, Writes: WriteRatio, CPU_Cores, AUS: AUSStr, Replication, ReqType: ReqTypeStr } = dv.current();
const requestPerServer = CPU_Cores / 0.5;

// Convert AUS string to number
const AUS = parseInt(AUSStr.replace(/,/g, ''), 10);

// Convert AFRS string to an array of numbers
const AFRSArray = AFRSStr.split(',').map(Number);

// Convert FeatName string to an array of names
const FeatNameArray = FeatNameStr.split(',');

// Convert FeatType string to an array of req
const ReqTypeArray = ReqTypeStr.split(',');

// Average Feature Total Request Size Per User
const AFTRS = AFRSArray.reduce((sum, val) => sum + val, 0);

// Estimation
const writesPerMonth = 30 * AFTRS * AUS;
const writesPerDay = writesPerMonth / 30;
const writesPerSec = writesPerDay / 86400;

// Long Term Estimates
const dataReplication = writesPerMonth * Replication;
const yearStorage = 12 * dataReplication;
const fiveYearStorage = yearStorage * 5;

// Network Traffic
const readsPerMonth = ReadRatio * writesPerMonth;
const readsPerDay = ReadRatio * writesPerDay;
const readsPerSec = ReadRatio * writesPerSec;

// Overall Traffic Calculations
const secondsInMonth = 30 * 86400;
const secondsInDay = 86400;

const overallMonthlyTraffic = (readsPerSec + writesPerSec) * AUS * secondsInMonth;
const overallDailyTraffic = (readsPerSec + writesPerSec) * AUS * secondsInDay;
const overallTrafficPerSec = (readsPerSec + writesPerSec) * AUS;

// Memory Cache
const cacheMemory = readsPerDay * AFTRS * 0.2;
const totalMemory = cacheMemory * Replication;

// Convert bytes to higher units for readability
const monthlyEstimationReadable = formatBytes(writesPerMonth);
const writesPerDayReadable = formatBytes(writesPerDay);
const dataReplicationReadable = formatBytes(dataReplication);
const yearStorageReadable = formatBytes(yearStorage);
const fiveYearStorageReadable = formatBytes(fiveYearStorage);
const readsPerMonthReadable = formatBytes(readsPerMonth);
const readsPerDayReadable = formatBytes(readsPerDay);
const overallMonthlyTrafficReadable = formatBytes(overallMonthlyTraffic);
const overallDailyTrafficReadable = formatBytes(overallDailyTraffic);
const overallTrafficPerSecReadable = formatBytes(overallTrafficPerSec);
const cacheMemoryReadable = formatBytes(cacheMemory);
const totalMemoryReadable = formatBytes(totalMemory);
const incomingDataPerSecReadable = formatBytes(writesPerSec * AFTRS);
const outgoingDataPerSecReadable = formatBytes(readsPerSec * AFTRS);

dv.paragraph(`#### Storage`);
dv.paragraph(`Let's say our total active users are **${AUS.toLocaleString()}**`);
dv.paragraph("<br>");
dv.paragraph(`***As a user, we want a feature to:***`);
dv.paragraph(`- **${ReqTypeArray[0]}** *${FeatNameArray[0]}* feature with an average size of **${formatBytes(AFRSArray[0])}**`);
dv.paragraph(`- **${ReqTypeArray[1]}** *${FeatNameArray[1]}* feature with an average size of **${formatBytes(AFRSArray[1])}**`);
dv.paragraph(`- **${ReqTypeArray[2]}** *${FeatNameArray[2]}* feature with an average size of **${formatBytes(AFRSArray[2])}**`);
dv.paragraph("<br>");
dv.paragraph(`##### Writes`);
dv.paragraph(`The total write request size, including metadata, is **${formatBytes(AFTRS)}**`);
dv.paragraph("<br>");
dv.paragraph(`Writes per month: **${monthlyEstimationReadable}**`);
dv.paragraph(`Writes per day: **${writesPerDayReadable}**`);
dv.paragraph(`Writes per second: **${formatBytes(writesPerSec * AFTRS)}**`);

dv.paragraph("<br>");
dv.paragraph(`Total storage needed after data replication: **${dataReplicationReadable}**`);
dv.paragraph(`Total storage for a year: **${yearStorageReadable}**`);
dv.paragraph(`Total storage for 5 years: **${fiveYearStorageReadable}**`);
dv.paragraph("<br>");
dv.paragraph(`### Network Traffic`);
dv.paragraph(`*Read*:Write ratio = *${ReadRatio}*:${WriteRatio} (read-heavy system)`);
dv.paragraph("<br>");
dv.paragraph(`##### Reads`);
dv.paragraph(`Reads per month: **${readsPerMonthReadable}**`);
dv.paragraph(`Reads per day: **${readsPerDayReadable}**`);
dv.paragraph(`Reads per second: **${formatBytes(readsPerSec * AFTRS)}**`);
dv.paragraph("<br>");
dv.paragraph(`Overall traffic per month: **${overallMonthlyTrafficReadable}**`);
dv.paragraph(`Overall traffic per day: **${overallDailyTrafficReadable}**`);
dv.paragraph(`Overall traffic per second: **${overallTrafficPerSecReadable}**`);
dv.paragraph("<br>");
dv.paragraph(`### Memory Cache`);
dv.paragraph(`Cache memory needed per day: **${cacheMemoryReadable}**`);
dv.paragraph("<br>");
dv.paragraph(`Total memory per day including replication: **${totalMemoryReadable}**`);
dv.paragraph("<br>");
dv.paragraph(`### Bandwidth`);
dv.paragraph(`Incoming data writes per second: **${incomingDataPerSecReadable}**`);
dv.paragraph("<br>");
dv.paragraph(`Outgoing data reads per second: **${outgoingDataPerSecReadable}**`);
dv.paragraph("<br>");
dv.paragraph(`### App Server Estimations`);
dv.paragraph(`**${CPU_Cores}** physical CPU cores`);
dv.paragraph(`**${requestPerServer.toFixed(2)}** requests per second for a single server`);
const numServer = Math.ceil(readsPerSec / requestPerServer);
dv.paragraph(`**${numServer}** servers needed`);
```


In any software system, failures are inevitable. These failures can arise from various factors such as bugs, traffic spikes, security issues, hardware failures, natural disasters, or even human error. While failures are a natural part of any system's lifecycle, they offer valuable learning opportunities. A postmortem is a structured tool used by tech teams to analyze failures and prevent them from recurring.
My First Postmortem

Issue Summary:

    Duration: The outage occurred on August 15, 2024, from 7:00 PM to 8:30 PM GMT.
    Impact: The system responsible for real-time football match analysis became unresponsive, affecting approximately 75% of users. Coaches and analysts were unable to access live data, which is critical during ongoing matches. Fans also experienced delays in receiving player performance updates.
    Root Cause: The root cause of the outage was a failure in the integration with the third-party API providing live match data. The API reached its request limit due to an unexpected surge in traffic, causing the system to stop receiving necessary data inputs.

Timeline:

    7:00 PM: The issue was first detected through an automated monitoring alert indicating that data retrieval from the external API had failed.
    7:05 PM: The development team was notified, and initial investigations began, focusing on potential network issues.
    7:15 PM: The team assumed that internal network congestion might be the problem and investigated the network infrastructure.
    7:30 PM: Upon further investigation, it was identified that the external API had exceeded its request quota, leading to a halt in data flow.
    7:35 PM: The incident was escalated to the DevOps team, who began communicating with the third-party API provider.
    8:00 PM: A temporary workaround was implemented by switching to a cached data system while waiting for the API request limits to reset.
    8:30 PM: The issue was resolved, and the system returned to normal operation after increasing the API request quota and resuming live data feeds.

Root Cause and Resolution:

    Root Cause: The system’s reliance on a single external API for live data was the primary vulnerability. The API reached its maximum request threshold due to an unexpected spike in user demand during a high-profile match.
    Resolution: The immediate solution involved switching to cached data to maintain service availability. A long-term solution was implemented by negotiating with the API provider to increase the request limits and developing an internal fallback system to handle data requests in case of future API failures.

Corrective and Preventative Measures:

    Improvements:
        API Quota Management: Implement more robust monitoring of API usage to preemptively avoid hitting request limits.
        Redundancy: Introduce redundancy by integrating multiple data sources so that the system can failover to an alternative API if the primary one fails.
        Caching System: Develop an advanced caching mechanism that allows for continuous operation with slightly outdated data when live data is unavailable.
    Tasks:
        Increase API Request Quota: Work with the API provider to secure a higher request limit to accommodate spikes in demand.
        Add API Usage Monitoring: Implement real-time monitoring and alerts for API usage to prevent future overages.
        Develop Fallback Mechanism: Create a fallback system that can switch between data sources seamlessly.
        Enhance Documentation: Update internal documentation to include procedures for handling API outages and other critical failures.
# OneDrive troubleshooting

## OneDrive file fetching not working

For anyone still working on this issue, the following is the reply from OneDrive support that corrected the problem for me:

1. Open OneDrive app settings:
2. Select Settings tab and make sure that there's a tick on _"Let me use OneDrive to fetch any of my files on this PC"_ checkbox and click OK.
3. Exit OneDrive app:
4. Now open registry editor:
5. Navigate to `HKEY_CURRENT_USER\SOFTWARE\Microsoft\OneDrive\`
6. Inside OneDrive location, right click on Claims folder and click Delete.
7. Start OneDrive:
8. Open OneDrive app settings:
9. Confirm that _"Let me use OneDrive to fetch any of my files on this PC"_ is still has a tick on it.


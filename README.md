# README.md

### Testing
1. Flux suddenly stopped. Changes of deployment were made (increased replica manually in OKD, not in GitLab) <br><br>
&emsp; After starting Flux, it decreased replica, following configs in GitLab <br><br>
2. Target folder, which is tracked by Flux, renamed in another project, but Flux configs still looking for previous name <br><br>
&emsp; Flux **didn't** delete any resource even if folder was changed by renaming. After changing configs in Flux, it uploaded actual state (i.e. while renaming folder, the replica count was increased from 1 to 3).

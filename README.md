# grafana_ibmi
trying to have grafana frontend working on IBMi

This repo will contain only the code changes to get grafana frontend working on IBMi. Not the full grafana code from https://github.com/grafana/grafana.git.




## LIMITS

Due to rust compiler not available on IBMi, the nx package manager is not able to build the grafana frontend.
It means that we need to do the same workaround as mentionned for freebsd : https://github.com/grafana/grafana/issues/89055

    yarn run themes-generate => only this part for now works fine 
    #yarn run generate-icons  => seems to use nx package manager, not working on IBMi
    #yarn workspaces foreach --include="@grafana-plugins/*" --parallel -A run build => not working for now, not investigated yet
    NODE_ENV=production yarn exec webpack --config scripts/webpack/webpack.prod.js --progress => fails



## current status

For now yarn run build fails at 92% with the following error : javascript heap out of memory when processing SourceMapDevToolPlugin.

same issue using :

    cd grafana
    make build-js


# k8s-express-test

      - name: Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: 'ghcr.io/${{ github.repository }}/k8s-express-test:${{ steps.short-sha.outputs.sha }}'
          format: 'template'
          template: '@/contrib/sarif.tpl'
          output: 'trivy-results.sarif'
  
      - name: Upload Trivy scan results to GitHub Security tab
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: 'trivy-results.sarif'
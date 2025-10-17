# Delete-deployment
清除历史工作流
你可以创建一个 GitHub Action，在下一次提交时自动删除部署（从这个回复中）。 例如，如果有一个部署到 GitHub Pages，你可以在工作流中添加以下条目。
jobs:
  cleanup:
    runs-on: ubuntu-latest
    permissions: write-all

    steps:
      - name:  Delete deployment
        uses: strumwolf/delete-deployment-environment@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          environment: github-pages
          onlyRemoveDeployments: true
          
此操作将删除指定环境（github-pages）上的所有现有部署。
在部署之前应运行此操作，以便环境中没有部署记录，并且随后运行的部署将只创建1个记录。

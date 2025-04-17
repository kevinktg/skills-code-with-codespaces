### You are learning about codespaces!
on_add_dependency:
  name: On Add dependency
  needs: get_current_step

  if: >-
    ${{ !github.event.repository.is_template
        && needs.get_current_step.outputs.current_step == 1 }}

  runs-on: ubuntu-latest

  steps:
    - name: Checkout
      uses: actions/checkout@v4
      with:
        fetch-depth: 0

    # Explicitly set the file and search inputs
    - name: Check workflow contents, jobs
      uses: skills/action-check-file@v1
      with:
        file: "index.html" # Ensure this file exists in the repo
        search: "Hello from codespace" # Correct the string value

    - name: Update to step 2
      uses: skills/action-update-step@v2
      with:
        token: ${{ secrets.GITHUB_TOKEN }}
        from_step: 1
        to_step: 2
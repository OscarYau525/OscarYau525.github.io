---
# Leave the homepage title empty to use the site title
title: ''
date: 2022-10-24
type: landing

sections:
  # About block
  - block: about.avatar
    id: about
    content:
      title: About Me
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
    design:
      biography:
        style: ''
  # Paper block
  - block: paper
    content:
      title: Accomplishments
      subtitle: ''
      text: 'Hi'
      # Date format: https://wowchemy.com/docs/customization/#date-format
      date_format: Jan 2006
      # Accomplishments.
      #   Add/remove as many `items` blocks below as you like.
      #   `title`, `organization`, and `date_start` are the required parameters.
      #   Leave other parameters empty if not required.
      #   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
      items:
        - title: Neural Networks and Deep Learning
          certificate_url: https://www.coursera.org
          date_end: ''
          date_start: '2021-01-25'
          description: ''
          icon: coursera
          organization: Coursera
          organization_url: https://www.coursera.org
          url: ''
        - title: Blockchain Fundamentals
          certificate_url: https://www.edx.org
          date_end: ''
          date_start: '2021-01-01'
          description: Formulated informed blockchain models, hypotheses, and use cases.
          icon: edx
          organization: edX
          organization_url: https://www.edx.org
          url: https://www.edx.org/professional-certificate/uc-berkeleyx-blockchain-fundamentals
        - title: 'Object-Oriented Programming in R'
          certificate_url: https://www.datacamp.com
          date_end: '2020-12-21'
          date_start: '2020-07-01'
          description: ''
          icon: datacamp
          organization: DataCamp
          organization_url: https://www.datacamp.com
          url: ''
    design:
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '2'

  # Publication block
  # - block: collection
  #   content:
  #     title: Recent Publications
  #     text: |-
  #       {{% callout note %}}
  #       Quickly discover relevant content by [filtering publications](./publication/).
  #       {{% /callout %}}
  #     filters:
  #       folders:
  #         - publication
  #       exclude_featured: true
  #   design:
  #     columns: '2'
  #     view: citation
---

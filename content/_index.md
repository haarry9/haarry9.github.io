---
# Leave the homepage title empty to use the site title
title: "Harishankar P V"
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography # to show intrest and education change to resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download Resume
        url: uploads/resume.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: new_bg.png
          filters:
            brightness: 0.6
          size: cover
          position: center
          parallax: true
  # - block: resume-skills
  #   content:
  #     title: Skills & Hobbies
  #     # Note: `username` refers to the user's folder name in `content/authors/`
  #     username: admin
  - block: markdown
    content:
      title: '📚 My Mission'
      subtitle: ''
      text: |-
        I'm a computer science engineer with a passion for **data science** and **AI**. I am also an enthusiatic coder profient in **Python** and **SQL**. I blog about data science, machine learning, deep learning techniques and business cases.

        I am dedicated to harnessing the power of data to uncover insights, drive innovation, and solve complex business problems. I apply a range of **data visualization** and **statistical analysis** techniques to interpret data, and use **machine learning algorithms** to extract meaningful patterns in data that can address business problems. I am committed to continuous learning and staying at the forefront of technological advancements to tackle real-world challenges.
   
        Please reach out to collaborate 😃
      button:
          text: Get Started
          url: https://hugoblox.com/templates/
    design:
      columns: '1'
      card:
        # Card background color (CSS class)
        css_class: "bg-primary-500"
        css_style: ""
  - block: cta-button-list
    content:
      # Need a custom icon?
      # Add an SVG image to the `assets/media/icons/` folder and reference it in the `icon` field below
      buttons:
        - text: 👉 Read my latest blog on Data Preprocessing Techniques
          # icon: academicons/arxiv
          url: https://arxiv.org/abs/2304.01852
        # - text: Watch my new YouTube video to achieve 20x productivity
        #   icon: brands/youtube
        #   url: https://youtube.com
        - text: Connect with me on LinkedIn
          icon: brands/linkedin
          url: https://linkedin.com
  - block: collection
    id: papers
    content:
      title: Featured Projects
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2
  # - block: collection
  #   id: papers
  #   content:
  #     title: Featured Publications
  #     filters:
  #       folders:
  #         - publication
  #       featured_only: true
  #   design:
  #     view: article-grid
  #     columns: 2
  # - block: collection
  #   content:
  #     title: Recent Publications
  #     text: ""
  #     filters:
  #       folders:
  #         - publication
  #       exclude_featured: false
  #   design:
  #     view: citation
  # - block: collection
  #   id: talks
  #   content:
  #     title: Recent & Upcoming Talks
  #     filters:
  #       folders:
  #         - event
  #   design:
  #     view: article-grid
  #     columns: 1
  - block: collection
    id: news
    content:
      title: Recent Blogs
      subtitle: ''
      text: ''
      # Page type to display. E.g. post, talk, publication...
      page_type: post
      # Choose how many pages you would like to display (0 = all pages)
      count: 5
      # Filter on criteria
      filters:
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc 
    design:
      # Choose a layout view
      view: date-title-summary
      # Reduce spacing
      spacing:
        padding: [0, 0, 0, 0]
  - block: cta-card
    demo: false # Only display this section in the Hugo Blox Builder demo site
    content:
      title: 👉 Get In Touch
      text: |-
        I'm available to collaborate on data science & machine learning projects, so feel free to contact me. If you have a question or want to say hello, I'll do my best to reply as quickly as possible.
      button:
        text: Say Hello
        url: 'mailto:hspv99@gmail.com'
    design:
      card:
        # Card background color (CSS class)
        css_class: "bg-primary-700"
        css_style: ""
---

<template>
  <div class="sidebar-container">
    <div class="sidebar-title"></div>
    <ul class="sidebar-links">
    </ul>
  </div>
</template>

<script>

export default {
  mounted: function() {
    var titleContainer = document.querySelector('.sidebar-title')
    var bigTitle = document.querySelector('h1')
    bigTitle = this.trim(bigTitle)
    titleContainer.appendChild(bigTitle)

    var titles = this.findTitles()
    titles = this.showToc(titles)
    window.addEventListener('scroll', () => {
      this.refreshToc(titles)
    })
  },

  methods: {
    trim(item) {
      var text = item.childNodes[1].nodeValue.trim()
      text = document.createTextNode(text)
      return text
    },
    findTitles() {
      var titles = document.querySelectorAll('h2, h3')
      return titles
    },
    showToc(titles) {
      var container = document.querySelector('.sidebar-links')
      titles.forEach(function(item) {
        var text = item.childNodes[1].nodeValue.trim()
        text = document.createTextNode(text)
        var textLink = document.createElement('a')
        textLink.appendChild(text)
        textLink.href = '#' + item.id
        var tocItem = document.createElement('li')
        tocItem.appendChild(textLink)
        if (item.tagName == 'H2') {
          tocItem.classList.add('sidebar-title2')
        } else {
          tocItem.classList.add('sidebar-title3')
        }
        container.appendChild(tocItem)
        item.toToc = tocItem
      })
      return titles
    },
    refreshToc(titles) {
      var scrollTop = document.documentElement.scrollTop || document.body.scrollTop
      var scrollBottom = scrollTop + document.documentElement.clientHeight
      var pageHeight = document.documentElement.scrollHeight
      titles.forEach(function(item, i) {
        if (scrollTop >= item.offsetTop) {
          item.toToc.classList.add('is-active')
          // Set others to inactive
          titles.forEach(function(item_sub, j) {
            if (j != i) {
              item_sub.toToc.classList.remove('is-active')
            }
          })
          // Set the parent h2 to active
          for (var k = i; k >= 0; k--) {
            if (titles[k].tagName == 'H2') {
              titles[k].toToc.classList.add('is-active')
              break
            }
          }
        }
      })
      if (scrollBottom >= pageHeight) {
        titles.forEach(function(item) {
          item.toToc.classList.remove('is-active')
        })
        var lastItem = titles[titles.length-1]
        lastItem.toToc.classList.add('is-active')
        
        // Set the parent h2 to active
        for (var k = titles.length-1; k >= 0; k--) {
          if (titles[k].tagName == 'H2') {
            titles[k].toToc.classList.add('is-active')
            break
          }
        }
      }
    }
  }
}

find
</script>

<style>
.sidebar-container {
  position: fixed;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
  background-color: rgba(255,255,255,1);
  font-size: 0.9rem;
  padding: 1rem 1.4rem;
  z-index: 30;
  transition: all 400ms;
}
@media screen and (min-width: 752px) {
  .sidebar-container {
    top: 0;
    bottom: 0;
    right: 0;
    min-width: 300px;
    box-shadow: 0px 5px 30px 0px rgba(0,0,0,0.2);
  }
}
@media screen and (max-width: 751px) {
  .sidebar-container {
    top: 0;
    bottom: 0;
    right: 0;
    width: 65%;
    box-shadow: 0px 5px 30px 0px rgba(0,0,0,0.2);
  }
}
.sidebar-container * {
  transition: 0ms;
}

.sidebar-title {
  font-weight: bold;
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
}

.sidebar-title2 {
  margin: 0.1em 0em;
}
.sidebar-title2 a {
  color: grey;
}
.sidebar-title2.is-active a {
  font-weight: bold;
  color: #3a8fb7;
  border-bottom: 2px solid #3a8fb7;
}

.sidebar-title3 {
  margin: 0.1em 0em;
}
.sidebar-title3 a {
  color: grey;
}
.sidebar-title3 {
  margin-left: 1rem;
}
.sidebar-title3.is-active a {
  font-weight: bold;
  color: #3a8fb7;
}
</style>

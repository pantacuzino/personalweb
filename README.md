Assumptions:

- Platform is Mac
- You can run a docker container on platform

[Squid is running](https://github.com/sameersbn/docker-squid)

docker run --name squid -d --restart=always --publish 3128:3128 --volume /srv/docker/squid/cache:/var/spool/squid3 sameersbn/squid:3.3.8

[Squid accepts connections from local network](https://github.com/boot2docker/boot2docker/blob/master/doc/WORKAROUNDS.md)

VBoxManage controlvm "boot2docker-vm" natpf1 "tcp-port8000,tcp,,8000,,8000";

[Squid logs](https://github.com/sameersbn/docker-squid)

docker exec -it squid2 tail -f /var/log/squid3/access.log

[Squid instance IP]()

docker-machine ip default

[Create browser bookmark to execute JS](http://stackoverflow.com/questions/18872679/function-as-google-chrome-bookmark)
javascript:(function(){var d=document,e=d.getElementById("someElement");e.value="some value";})();

[Get selected text from the webpage in Chrome](http://stackoverflow.com/questions/3074630/get-the-selected-text-of-a-web-page-in-google-chrome-extension)

var selection = window.getSelection(); 
var range = selection.getRangeAt(0); 
if (range) { 
  var div = document.createElement('div'); 
  div.appendChild(range.cloneContents()); 
  alert(div.innerHTML); 
}

## Bookmarklet


### Copy selected text

javascript:(function(){if(!window.selections) { window.selections = new Array(); }; var s = window.getSelection(); var r = s.getRangeAt(0); if (r) { var d = document.createElement('div'); d.appendChild(r.cloneContents()); window.selections.push(d.innerHTML); } alert(window.selections);})();

### Send all selections to Squid

javascript:void((function(){var s=document.createElement('script');s.type='text/javascript';s.src='https://ajax.googleapis.com/ajax/libs/jquery/2.1.3/jquery.min.js';document.body.appendChild(s); $.get("http://nonexistenthost.com/", function(data) {}); })());

## Similar Users

[Mark Ashley Bell](http://markb.co.uk/building-a-simple-google-chrome-extension.html)
I have a web app running on my home server to keep track of my bookmarks—it's a little like Delicious, but simpler and with some personal customisations. Currently I save bookmarks to this app via a Javascript bookmarklet: clicking it gets the current page's title and url (and also any selected text, to use as a summary) and sends it to a popup form; submitting that form then saves the bookmark data to the server.

# Python_Live_Project

## Introduction

I was tasked to work on an app that let's you log and track certain aspects of a collection. Specifically, I chose to make an app to track a user's record collection. I worked with a few others that were also creating similiar apps for different topics. For this project, we used Django and Python to create dynamic apps that had a wide range of function.

## Creating a new album for the collection
```
  def album_add_view(request):
      if request.method == "POST":
          form = AlbumForm(request.POST)
          if form.is_valid():
              form.save()
              return redirect('albumList')
      else:
          form = AlbumForm()
      return render(request, "VinylCollection/Album_Add.html", {'form': form})
```
## Itunes API

It took me quite a while to find an API that was suitable for this project and was not overly complex. At first, I was intending to use Discogs API but later discovered that the Itunes API would work seemlessly for my project.
```
  def api_search(request):
      response = requests.get('https://itunes.apple.com/search?')
      context = response.json()
      if request.method == 'POST':
          if 'album' in request.POST:
              find_album = request.POST['album']
              response = requests.get('https://itunes.apple.com/search?entity=album&term={}'.format(find_album))
              context = print(response.json())
              return render(request, 'VinylCollection/Album_API.html', context)
      return render(request, 'VinylCollection/Album_API.html', context)
 ```
 ## Skills learned
Through working on this project I now understand Django and web developement to a much greater extent than I did before. Processing POSTs, REQUESTs, and GETs has tremendously help wrap my head around how website work and how information flows from one page to another.

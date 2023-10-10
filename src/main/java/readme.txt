RecentlyPlayedStore Class:

1. RecentlyPlayedStore is a class that stores recently played songs for each user and has a fixed capacity defined by the initialCapacity.
It uses a Map<String, List<String>> called userSongsMap to store user names as keys and a list of recently played songs as values.
The addSong method allows adding a song for a specific user. It uses computeIfAbsent to create a list for a user if it doesn't exist and adds the song to that list.
The fixedCapacity method ensures that the stored songs don't exceed the specified capacity. If the number of users songs exceeds the capacity, it removes the least recently played song.
The RecentlyPlayed method returns the recently played songs for a given user.


RecentSongs Class:
2. RecentSongs is a class with a main method where an instance of RecentlyPlayedStore is created with an initial capacity of 2.
Several songs are added to different users using the addSong method of the RecentlyPlayedStore.
The user is prompted to enter a username, and the RecentlyPlayed method is called to display the recently played songs for the specified user.


Overall, this code tells a simple recently played song store for multiple users, limiting the number of stored songs for each user based on the initial capacity. When the capacity is exceeded, it removes the least recently played user's songs to accommodate new songs.

import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.List;
import java.util.Map;

class PlaySong {
    private final int initialCapacity;
    private final Map<String, List<String>> userSongsMap;

    public RecentlyPlayedStore(int initialCapacity) {
        this.initialCapacity = initialCapacity;
        this.userSongsMap = new LinkedHashMap<>(initialCapacity, 0.75f, true);
    }

    public void addSong(String user, String song) {
        userSongsMap.computeIfAbsent(user, k -> new LinkedList<>()).add(song);
        maintainCapacity();
    }

    public List<String> getRecentlyPlayed(String user) {
        return userSongsMap.getOrDefault(user, new LinkedList<>());
    }

    private void maintainCapacity() {
        if (userSongsMap.size() > initialCapacity) {
            String leastRecentlyPlayedUser = userSongsMap.keySet().iterator().next();
            userSongsMap.remove(leastRecentlyPlayedUser);
        }
    }
}

public class RecentSongs {
    public static void main(String[] args) {
        PlaySong store = new PlaySong(3);

        store.addSong("user1", "Song1");
        store.addSong("user1", "Song2");
        store.addSong("user2", "Song3");
        store.addSong("user3", "Song4");
        store.addSong("user2", "Song5");
        Scanner sc= new Scanner(System.in);
        System.out.print("Enter user Name to Know which song recently played buy that user : ");

        System.out.println("Recently played songs for user1: " + store.getRecentlyPlayed("user1"));
        System.out.println("Recently played songs for user2: " + store.getRecentlyPlayed("user2"));
        System.out.println("Recently played songs for user3: " + store.getRecentlyPlayed("user3"));
    }
}

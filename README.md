class Song:
    def __init__(self,data):
        self.data=data
        self.next=None

class playlist:
    def __init__(self):
        self.head=None

    def is_empty(self):
        return self.head is None
   
    def append(self,data):
        new_song=Song(data)
        if self.head is None:
            self.head=new_song
            return
        current=self.head
        while current.next:
            current=current.next
        current.next=new_song
   
    def prepend(self,data):
        new_song=Song(data)
        new_song.next=self.head
        self.head=new_song

    def delete(self,data):
        if self.head is None:
            return
        if self.head.data==data:
            self.head=self.head.next
            return
        current=self.head
        while current.next:
            if current.next.data==data:
                current.next=current.next.next
                return
            current=current.next
   
    def insert(self,data,prev):
        song=Song(data)
        current=self.head
        while current:
            if current.data==prev:
                song.next=current.next
                current.next=song
                return
            current=current.next
        return

    def Search(self,data):
        current=self.head
        while current:
            if current.data==data:
                print("song available")
                return
            current=current.next
        print("SONG NOT AVAILABLE")
        return
   
    def display(self):
        current=self.head
        while current:
            print(current.data,end="\n")
            current=current.next
        print("\n--END OF DRUGS--\n")
Pl=playlist()
Pl.append("god mode")
Pl.append("oorum blood")
Pl.append("pavazhamalli")
print("playlist")
Pl.display()
Pl.prepend("karuppu kooda vara da")
print("After update")
Pl.display()
Pl.insert("nallaru poo ","god mode")
Pl.display()
Pl.delete("oorum blood")
print("After delete")
Pl.display()
Pl.Search("god mode")
print("searching element")

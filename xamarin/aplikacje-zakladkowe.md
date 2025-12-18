# Aplikacje zakładkowe 
W Xamarin.Forms głównym kontenerem dla zakładek jest element TabbedPage w pliku MainPage.xaml . To właśnie tam modyfikujemy i dodajemy zakładki do naszej aplikacji.

# Krok 1: Stwórz podstrony
Przygotuj nową stronę: Stwórz nową stronę (np. prawy przycisk myszy na projekt -> Add -> New Item -> Content Page) i nazwij ją np. Page1.xaml.

# Krok 2: Przygotuj MainPage.xaml
Zdefiniuj przestrzeń nazw (jeśli nowa strona jest w innym folderze): Upewnij się, że w nagłówku TabbedPage masz zadeklarowane xmlns:mypages="clr-namespace:TwojaNazwaProjektu".

Musisz zmienić główny kontener strony z ContentPage na TabbedPage. Otwórz MainPage.xaml i zamień początkowy tag

MainPage.xaml:
```
<TabbedPage xmlns="http://xamarin.com/schemas/2014/forms"
            xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
            xmlns:mypages="clr-namespace:TwojaNazwaProjektu"
            x:Class="TwojaNazwaProjektu.MainPage">
```
# 3 Krok
Dodaj element strony: Wewnątrz znaczników ```<TabbedPage> ... </TabbedPage>``` dopisz nową zakładkę:

MainPage.xaml:
``` 
<TabbedPage.Children>
    <mypages:Page1 Title="Opis"></mypages:Page1>
    <mypages:Page2 Title="Kalkulator"></mypages:Page2>
</TabbedPage.Children>
```
W podanym przykładzie tworzymy aplikacje zakładkową z 2 zakładkami o nazwach Opis i Kalkulator. Pozwala nam to na korzystanie z dwóch osobnych podstron naszej aplikacji.

# 4 Krok 

Również w pliku Mainpage.xaml.cs w klasie  należy zmienić z ContentPage na TabbedPage:

MainPage.xaml.cs
```cs
public  partial class MainPage : TabbedPage
{
    public MainPage()
    {
         InitializeComponent();
    }

}
```

# O czym musisz pamiętać?
Właściwość Title: To najważniejszy atrybut. Jeśli go pominiesz, zakładka może się pojawić, ale nie będzie na niej żadnego tekstu.

Istnieje możliwość, że w poleceniu trzeba będzie dodać ikone do zakładek, wtedy używamy atrybutu: 
```
IconImageSource="ikona.png"
```
Pliki ikon należy umieścić w katalogu Resources (Android/iOS)


Kolejność: Zakładki wyświetlają się w takiej kolejności, w jakiej są zapisane w kodzie (od góry do dołu w XAML).

MainPage.xaml MUSI dziedziczyć po TabbedPage.

Strony muszą dziedziczyć po ContentPage.
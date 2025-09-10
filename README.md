**[View document in Syncfusion .NET MAUI Knowledge Base](https://www.syncfusion.com/kb/13127/how-to-use-uri-images-in-net-maui-listview-sflistview)**

## Sample

```xaml
<ListView:SfListView x:Name="listView" ItemSize="60" ItemsSource="{Binding ContactsInfo}">
    <ListView:SfListView.ItemTemplate >
        <DataTemplate>
            <Frame Padding="2" Margin="2" HasShadow="False" BorderColor="LightGray">
                <Grid x:Name="grid" RowSpacing="0">
                    <Image HeightRequest="50" WidthRequest="50" HorizontalOptions="CenterAndExpand" VerticalOptions="CenterAndExpand" Aspect="AspectFit">
                        <Image.Source>
                            <UriImageSource Uri="{Binding ContactImage}" CacheValidity="1" CachingEnabled="true"/>
                        </Image.Source>
                    </Image>
                </Grid>
            </Frame>
        </DataTemplate>
    </ListView:SfListView.ItemTemplate>
</ListView:SfListView>

ViewModel.cs:

public ObservableCollection<Contacts> ContactsInfo { get; set; }

public ContactsViewModel()
{
    ContactsInfo = new ObservableCollection<Contacts>();
    GenerateInfo();
}

public void GenerateInfo()
{
    Random r = new Random();
    for (int i = 0; i < 40; i++)
    {
        var contact = new Contacts(CustomerNames[i], r.Next(720, 799).ToString() + " - " + r.Next(3010, 3999).ToString());
        contact.ContactImage = "https://upload.wikimedia.org/wikipedia/commons/thumb/1/12/User_icon_2.svg/220px-User_icon_2.svg.png";
        ContactsInfo.Add(contact);
    }
}
```

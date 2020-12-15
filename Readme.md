

## Fungctionality
- User dapat memilih menu makanan.
- User dapat menghapus makanan yang telah dipilih.

## How does it works?
```csharp
private void onButtonAddItemClicked(object sender, RoutedEventArgs e)
        {
            Penawaran penawaranWindow = new Penawaran();
            penawaranWindow.SetOnItemSelectedListener(this);
            penawaranWindow.Show();
        }
```
digunakan untuk membuka menu penawaran

```csharp
public void addItem(Item item)
        {
            this.itemBelanja.Add(item);
            this.callback.addItemSucceed();
            calculateSubTotal();
        }
```
digunakan untuk menambahkan item ke keranjang

```csharp
private void calculateSubTotal()
        {
            double subtotal = 0;
            foreach (Item item in itemBelanja)
            {
                subtotal += item.price;
            }
            payment.updateTotal(subtotal);

        }
```
digunakan untuk menghitung sub total barang yang akan di beli

```csharp
public void removeItem(Item item)
        {
            this.itemBelanja.Remove(item);
            this.callback.removeItemSucceed();
            calculateSubTotal();
        }
```
digunakan untuk menghapus menu yang sudah di masukkan kedalam 
keranjang
 
```csharp
 public void updateTotal(double subtotal)
        {
            double total = subtotal + deliveryFee - promo;
            this.balance = this.balance - total;
            this.paymentCallback.onPriceUpdated(subtotal,  total, balance);
        }

```
digunakan unutuk menghitung hasil total semua dan mengurangi balance 
kita sesuai dengan total harga barang yang di beli

# Addresses

| Address                                          | Description                                                                                                                                                                                                     | Tonscan link                                                           |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| EQAhE6welE8-KaHuIEEISESFQOh-X0pVjkjYv1hl_wq7g0zg | Địa chỉ người dùng gửi tiền vào. Không phải ví thông thường ví thông thường phải có loại là `wallet v4 r2` gọi là `SnakeTONVault`. Hiện tại không biết cụ thể contract logic vì tác giả chưa public source code | https://tonviewer.com/EQAhE6welE8-KaHuIEEISESFQOh-X0pVjkjYv1hl_wq7g0zg |
| UQACrQDYTWMkLgLedyOTx9hQk9HV-QfXVXthOvV0eOdzYBsM | Đỉa chỉ của owner + deployer của ví người dùng gửi tiền vào                                                                                                                                                     | https://tonviewer.com/EQACrQDYTWMkLgLedyOTx9hQk9HV-QfXVXthOvV0eOdzYEbJ |

## Methods

| Method     | Description                   | Example TONScan link                                                                                                                |
| ---------- | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 0x612da2bb | `withdraw()` dùng để rút tiền | https://tonviewer.com/transaction/88c672c4ead2378af469be11026b25ea1368d2274f50f6849fe32463566e9d90. Do owner gọi hàm để gửi tiền ra |
| 0xcd28a5a0 | `deposit()` dùng để nạp tiền  | https://tonviewer.com/transaction/e004c4d965d6dff7bc5f282e432347f7b19ae2d9a36b52154e66399fa73cb650. Do người dùng gửi tiền vào      |

![deposit](deposit.png)
![withdraw](withdraw.png)

## F&Q

- Làm sao biết được ai đang có bao nhiều tiền?
  - Lưu ở database web2. Sau khi chơi game xong cũng cộng trừ bình thường trong web2

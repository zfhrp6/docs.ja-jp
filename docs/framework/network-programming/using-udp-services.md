---
title: "UDP サービスの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "プロトコル、UDP"
  - "ネットワーク リソース、UDP"
  - "要求 (インターネットからデータを)、UDP"
  - "UDP"
  - "受信 (データを)、UDP"
  - "インターネット、UDP"
  - "複数のアドレスへのメッセージのブロードキャスト"
  - "データ要求、UDP"
  - "UdpClient クラス、UdpClient クラスについて"
  - "送信 (データを)、UDP"
  - "アプリケーション プロトコル、UDP"
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# UDP サービスの使用
<xref:System.Net.Sockets.UdpClient> のクラスは、UDP を使用してネットワーク サービスと通信します。  <xref:System.Net.Sockets.UdpClient> クラスおよびメソッドのプロパティは、UDP を使用してデータを要求と入荷の <xref:System.Net.Sockets.Socket> の作成の詳細を追加します。  
  
 ユーザー データグラム Protocol \(UDP\) はリモート ホストにデータを提供するのに最適な努力をする簡単なプロトコルです。  ただし、UDP プロトコルがコネクションレスなプロトコルであるため、リモート エンドポイントに送信される UDP データグラムが着荷対して保証する \(送信\) 同じ順序で到着に対して保証します。  UDP を使用するアプリケーションが不足している、重複および注文が狂ってデータグラムを処理するために準備する必要があります。  
  
 に UDP を使用してデータグラムを送信するには、通信するために、サービスを利用する UDP ポート番号必要なサービスをホストしているネットワーク デバイスのネットワーク アドレスを把握している必要があります。  インター ネット住所を \(Iana\) 管理、共通のサービスのポート番号を定義します \(www.iana.org\/assignments\/port\-numbers\) を参照してください。  Iana の一覧のサービスはない範囲 1,024 に 65,535 のポート番号を使用できます。  
  
 特別ネットワーク IP アドレスがベースのネットワーク UDP 配信メッセージをサポートするために使用されます。  次の議論は、インターネットで、例として使用される IP \(バージョン 4 の住所のファミリーを使用します。  
  
 IP \(バージョン 4 の住所がネットワーク アドレスを指定するには、32 ビットのコードを使用します。  255.255.255.0 の netmask を使用してクラス C の住所に、これらのオブジェクトは 4 人のオクテットに分けられます。  小数点以下 10 桁で表現した場合、4 人のオクテットは 192.168.100.2 など、知られた点を打クォードの表記を、フォームで行います。  最初の 2 人のオクテット \(この例では、192.168\) は、ネットワーク番号を、3 番目のオクテット \(100\) を定義します \(2\) によってホストの ID である最終オクテットとサブネットが表示されます。  
  
 1 種類の IP アドレスのすべてのオブジェクト、またはフォームの 255.255.255.255 制限されます。住所を設定します  この住所 UDP データグラムの送信は、ローカル ネットワークの区分のすべてのホストにメッセージを提供します。  このアドレスに送信される、ルーターの順方向メッセージの区分のネットワーク ホスト配信のみメッセージが表示されないので。  
  
 配信は、ネットワークの特定の部分でホストの ID のすべてのオブジェクトの設定によって指示できます。  たとえば、192.168.1 と開始する IP アドレスによって識別されるすべてのネットワーク ホストのに配信を送信するに 192.168.1.255 住所を使用します。  
  
 次のコード例は、ポート 11,000 の指示済配信 192.168.1.255 アドレスに送信される UDP データグラム聴覚にそばを立てるに <xref:System.Net.Sockets.UdpClient> を使用します。  クライアントはメッセージの文字列が表示され、コンソールに書き込んだり。  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 次の例は、ポート 11,000 コードを使用して指示済配信住所 192.168.1.255 に UDP データグラムを送信するに <xref:System.Net.Sockets.UdpClient> を使用します。  クライアントはコマンド ラインで指定されたメッセージの文字列を送信します。  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## 参照  
 <xref:System.Net.Sockets.UdpClient>   
 <xref:System.Net.IPAddress>   
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)
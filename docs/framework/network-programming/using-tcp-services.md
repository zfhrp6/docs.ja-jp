---
title: "TCP サービスの使用 | Microsoft Docs"
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
  - "要求 (インターネットからデータを)、TCP"
  - "受信 (データを)、TCP"
  - "TcpClient クラス、TcpClient クラスについて"
  - "データ要求、TCP"
  - "アプリケーション プロトコル、TCP"
  - "ネットワーク リソース、TCP"
  - "送信 (データを)、TCP"
  - "TCP"
  - "プロトコル、TCP"
  - "インターネット、TCP"
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# TCP サービスの使用
<xref:System.Net.Sockets.TcpClient> のクラスが TCP を使用してインターネットのリソースのデータが必要です。  **TcpClient** 方法およびプロパティは、TCP を使用してデータを要求と入荷の <xref:System.Net.Sockets.Socket> を作成するための詳細を追加します。  デバイスへのリモート接続がストリームとして示されるため、データが技術をストリーム処理と .NET Framework 読み取られ、作成できます。  
  
 次に TCP プロトコルは、データ パケットを送受信する接続エンドポイントと使用による接続を設定します。  TCP が着荷ときにデータ パケットがエンドポイントに送信され、正しい順序で組み立てことを確認する担当者があります。  
  
 TCP への接続を確立するには、必要な通信するために使用するサービスが TCP ポートはサービスをホストするネットワークのデバイスの住所がわかります。  インター ネット住所を \(Iana\) 管理、共通のサービスのポート番号を定義します \(www.iana.org\/assignments\/port\-numbers\) を参照してください。  Iana の一覧のサービスはない範囲 1,024 に 65,535 のポート番号を使用できます。  
  
 次の例では、TCP ポート 13 でタイム サーバーに接続する **TcpClient** が設定されていることを示します。  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <xref:System.Net.Sockets.TcpListener> がクライアントへの接続を管理する着呼要求の TCP ポートを監視し、**\[ソケット\]** を **TcpClient** を作成するために使用されます。  <xref:System.Net.Sockets.TcpListener.Start%2A> 方法がリッスン有効にし、<xref:System.Net.Sockets.TcpListener.Stop%2A> 方法でポートがリッスン無効にします。  <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> 方法は、フォワード接続を承認し、要求を処理するために **TcpClient** を作成および <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> 方法の承認を接続を要求の処理に **\[ソケット\]** を要求し、作成します。  
  
 次の例は、モニターの TCP ポート 13 に **TcpListener** を使用してネットワークのタイム サーバーを作成することを示します。  フォワード接続の要求が承認されると、タイム サーバーがホスト サーバーから現在の日時に回答します。  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```  
  
## 参照  
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)
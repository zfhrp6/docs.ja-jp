---
title: "バージョン 3.5 のソケット パフォーマンスの強化 | Microsoft Docs"
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
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# バージョン 3.5 のソケット パフォーマンスの強化
<xref:System.Net.Sockets.Socket?displayProperty=fullName> のクラスは、高性能を実現するために非同期なネットワークの I\/O を使用するアプリケーションに使用する Version 3.5 で高められました。  一連の新しいクラスは <xref:System.Net.Sockets.Socket> クラスに特別な高性能ソケット アプリケーションに使用できる代替非同期パターンを提供する一連の改良の一部として追加されました。  これらの高パフォーマンスを改善が必要なサーバー ネットワークのアプリケーションに合わせてデザインされています。  アプリケーションはアプリケーションの対象とした、地域の活動でのみ大量のデータを受け取る場合など\) 拡張非同期パターン、またはのみ使用できます \(。  
  
## クラスの改良  
 これらの強化部分の主な機能として、大量の非同期ソケット I\/O 操作時にオブジェクトの割り当てと同期の繰り返しを回避することが挙げられます。  非同期なソケット現在の I\/O の <xref:System.Net.Sockets.Socket> のクラスが実装される開始\/終了のデザイン パターンは、非同期のなソケットの工程に割り当てられます <xref:System.IAsyncResult?displayProperty=fullName> のオブジェクトを要求します。  
  
 新しい <xref:System.Net.Sockets.Socket> クラスの改良で、非同期の工程はソケットなアプリケーションで配賦され管理する <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=fullName> の再利用可能なオブジェクト クラスによって示されます。  高パフォーマンスのソケット アプリケーションは、維持する必要のある重複したソケット操作の量を十分に認識しています。  アプリケーションでは、必要な数の <xref:System.Net.Sockets.SocketAsyncEventArgs> オブジェクトを作成できます。  たとえば、サーバー アプリケーションは、受信するクライアント接続率をサポートするために、未払の 15 のソケットの承認の工程があるたびに必要がある場合は、その目的の <xref:System.Net.Sockets.SocketAsyncEventArgs> の 15 の再利用可能なオブジェクトを事前に割り当てることができます。  
  
 このクラスで非同期ソケット操作を実行するためのパターンは、次の手順で構成されます。  
  
1.  新しい <xref:System.Net.Sockets.SocketAsyncEventArgs> コンテキスト オブジェクトを割り当てるか、アプリケーション プールから空きオブジェクトを取得します。  
  
2.  実行する工程へのコンテキストでオブジェクトのプロパティを複数設定 \(コールバック指定方法、バッファ データなど\)。  
  
3.  適切なソケット メソッド \(xxxAsync\) を呼び出して、非同期操作を開始します。  
  
4.  非同期なソケット方法 \(xxxAsync\) がコールバック true、それを完了ステータスのコンテキスト プロパティを照会します。  
  
5.  非同期なソケット方法 \(xxxAsync\) がコールバック false を返す場合、工程は同期的に入力されます。  この場合、コンテキスト プロパティに操作の結果を照会できます。  
  
6.  コンテキストを別の操作に再利用するか、プールに戻すか、または破棄します。  
  
 新しい非同期なソケットの工程のコンテキストでは、アプリケーション オブジェクトの有効期間コードと非同期の I\/O 参照の参照によって決まります。  非同期ソケット操作コンテキスト オブジェクトが非同期ソケット操作メソッドのいずれかにパラメーターとして送信された後は、アプリケーションでこのオブジェクトへの参照を保持する必要はありません。  完了コールバックから制御が戻るまで、オブジェクトは参照されたままになります。  ただし、は、将来の非同期なソケットの工程で再利用できるよう、コンテキストのオブジェクトへの参照を終了アプリケーションの場合は有効です。  
  
## 参照  
 <xref:System.Net.Sockets.Socket?displayProperty=fullName>   
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=fullName>   
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)   
 [ソケットのパフォーマンス テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179570)
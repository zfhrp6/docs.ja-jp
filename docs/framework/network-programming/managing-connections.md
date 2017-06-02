---
title: "接続の管理 | Microsoft Docs"
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
  - "インターネット、接続"
  - "HTTP、クラス (接続用の)"
  - "要求 (インターネットからデータを)、接続"
  - "送信 (データを)、接続"
  - "受信 (データを)、接続"
  - "ServicePoint クラス、ServicePoint クラスの概要"
  - "インターネット要求への応答、接続"
  - "接続 [.NET Framework]、クラス"
  - "ネットワーク リソース、接続"
  - "ダウンロード (インターネット リソースの)、接続"
  - "ServicePointManager クラス、ServicePointManager クラスの概要"
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 接続の管理
データ リソースに接続して HTTP を使用するアプリケーションは、インターネットへの接続を管理し、最適なスケール、パフォーマンスの実現にするには、.NET フレームワークの <xref:System.Net.ServicePoint> と <xref:System.Net.ServicePointManager> クラスを使用できます。  
  
 **ServicePoint** クラスは、インターネットのリソースにアクセスするアプリケーションが接続できるエンドポイントをアプリケーションが提供されます。  各 **ServicePoint** は、パフォーマンスを改善するにヘルプが接続間の最適化情報を共有することで、インターネット サーバーがとの接続を最適化する情報が含まれます。  
  
 各 **ServicePoint** は Uniform Resource Identifier \(URI\) が確認され、URI の設定の ID とホストの片に従って並べ替えられます。  たとえば、**ServicePoint** 同じ URI のインスタンスは http:\/\/www.contoso.com\/index.htm、http:\/\/www.contoso.com\/news.htm?date\=today に同じ設定の ID \(http\) とホストの片 \(www.contoso.com\) がある要求を提供します。  既にアプリケーションにサーバーへの接続が www.contoso.com 耐久性がある場合、2 種類の接続を作成する必要が回避両方の要求を取得するためにその接続を使用します。  
  
 **ServicePointManager** は **ServicePoint** のインスタンスの作成と管理を破壊する静的クラスです。  **ServicePointManager** は、アプリケーションが **ServicePoint** のあるインスタンスのグループにない Internet のリソースが必要な場合 **ServicePoint** を作成します。  **ServicePoint** のインスタンスは最大のアイドル時間を超えた場合、または **ServicePoint** のあるインスタンスの数がアプリケーションの **ServicePoint** のインスタンスの最大数を超えた場合に、破壊されます。  **ServicePointManager**の <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> と <xref:System.Net.ServicePointManager.MaxServicePoints%2A> のプロパティの設定によって **ServicePoint** のインスタンスの既定の最大のアイドル時間と最大数の両方を制御できます。  
  
 クライアントとサーバー間の接続数は、アプリケーションのスループットの劇的な影響することができます。  既定では、<xref:System.Net.HttpWebRequest> クラスを使用してアプリケーションは最大特定のサーバーへの 2 種類の耐久性がある接続を使用して、アプリケーション基準の接続ごとの最大数を設定できます。  
  
> [!NOTE]
>  制限 HTTP\/1.1 標準アプリケーションからサーバー 1 通の 2 種類の接続に接続する番号。  
  
 接続の最適な番号は、アプリケーションで実行される実際の要件によって異なります。  使用可能なアプリケーションに接続の数は、増やすことは、アプリケーションのパフォーマンスに影響しない場合があります。  接続数を変えて中詳細に接続の影響を決定するため、実行パフォーマンステスト。  次のサンプル コードに示すように、アプリケーションでアプリケーションの初期設定に **ServicePointManager** クラスの <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> の静的なプロパティの変更で使用する接続数を変更できます。  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 **\[ServicePointManager.DefaultConnectionLimit\]** のプロパティを変更すると、前に **ServicePoint** の初期化したインスタンスには影響しません。  次のコードは `newLimit`に格納されている値にサーバーの http:\/\/www.contoso.com 既存の **ServicePoint** の接続の限度を変更することを示します。  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## 参照  
 [接続のグループ化](../../../docs/framework/network-programming/connection-grouping.md)   
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)
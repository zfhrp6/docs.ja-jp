---
title: "方法: データ サービス要求のクライアント資格情報を指定する (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 要求のカスタマイズ"
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: データ サービス要求のクライアント資格情報を指定する (WCF Data Services)
既定では、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに要求を送信する際、クライアント ライブラリから資格情報は提供されません。  ただし、<xref:System.Data.Services.Client.DataServiceContext> の <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> プロパティに <xref:System.Net.NetworkCredential> を設定することで、データ サービスへの要求を認証するために資格情報を送信するように指定できます。  詳細については、「[WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  このトピックの例では、データ サービスのデータを要求する際に [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントで使用する資格情報を明示的に提供する方法を示します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web サイトで公開されている [Northwind サンプル データ サービス](http://go.microsoft.com/fwlink/?LinkId=187426)を使用することもできます。このサンプル データ サービスは読み取り専用で、変更を保存しようとするとエラーが返されます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web サイトのサンプル データ サービスでは、匿名認証が許可されます。  
  
## 使用例  
 次の例は、Windows Presentation Framework アプリケーションのメイン ページである Extensible Application Markup Language \(XAML\) ファイルの分離コード ページからの抜粋です。  この例では、`LoginWindow` インスタンスを表示してユーザーから認証資格情報を収集し、データ サービスへの要求を行うときにこれらの資格情報を使用します。  
  
  
  
## 使用例  
 次の XAML は、WPF アプリケーションのメイン ページを定義します。  
  
  
  
## 使用例  
 次の例は、データ サービスへの要求を行う前にユーザーから認証資格情報を収集するために使用するウィンドウの分離コード ページからの抜粋です。  
  
  
  
## 使用例  
 次の XAML は、WPF アプリケーションのログインを定義します。  
  
  
  
## .NET Framework セキュリティ  
 このトピックの例には、以下のセキュリティに関する注意点があります。  
  
-   このサンプルで指定した資格情報が機能することを確認するには、Northwind データ サービスで匿名アクセス以外の認証方式を使用する必要があります。  そうしない場合、データ サービスをホストする Web サイトが資格情報を要求しません。  
  
-   ユーザー資格情報は実行時にのみ要求し、キャッシュしないようにする必要があります。  資格情報は常に安全に格納する必要があります。  
  
-   基本認証およびダイジェスト認証で送信されるデータは暗号化されないため、敵対者がデータを見ることができます。  また、基本認証の資格情報 \(ユーザー名とパスワード\) はクリア テキストで送信されるので、傍受される可能性があります。  
  
 詳細については、「[WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  
  
## 参照  
 [WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)   
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
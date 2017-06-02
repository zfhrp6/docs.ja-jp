---
title: "フォーム ポスト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# フォーム ポスト
このサンプルでは、WCF REST プログラミング モデルを拡張して新しい受信要求形式をサポートする方法を示します。  このサンプルには、要求を HTML フォーム ポストから [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型に逆シリアル化できるフォーマッタの実装も含まれています。  また、このサンプルでは T4 テンプレートを使用して、ユーザーが WCF REST サービスにポストバックできる HTML フォームを提供する HTML ページを返します。  
  
## 使用例  
  
-   受信要求形式のサポートの拡張。  
  
-   T4 テンプレートの統合。  
  
## 説明  
 このサンプルは、2 つのプロジェクトで構成されます。  1 つ目のプロジェクトは、HTML フォーム ポストを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型に逆シリアル化できるカスタム要求フォーマッタを含む HtmlFormProcessing ライブラリです。  2 つ目のプロジェクトは、HtmlFormProcessing ライブラリのカスタム要求フォーマッタを使用するように基本的なリソース サービス サンプルを拡張するコンソール アプリケーションです。  
  
 HTML フォーム ポストを逆シリアル化できるカスタム フォーマッタ \(HtmlFormRequestDispatchFormatter\) は、<xref:System.ServiceModel.Dispatcher.QueryStringConverter> を使用して文字列から変換できる [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型と、QueryStringConverter を使用して文字列から変換できるメンバーのみを持つ <xref:System.Runtime.Serialization.DataContractAttribute> でマークされた型の両方を受け入れます。  
  
 HtmlFormProcessing ライブラリ プロジェクトには、他のカスタム要求フォーマッタを作成するために使用できる抽象基本クラス `RequestBodyDispatchFormatter` も含まれています。  `RequestBodyDispatchFormatter` から派生させると、開発者は、基本クラスで URI テンプレート パラメーターを操作のメソッド パラメーターにマップできるようにする要求本文の逆シリアル化ロジックに集中できます。  また、HtmlFormProcessing ライブラリ プロジェクトには、<xref:System.ServiceModel.Description.WebHttpBehavior> から派生させて既定の要求フォーマッタをカスタム要求フォーマッタに置き換える方法を示す `HtmlFormProcessingBehavior` クラスもあります。  
  
 このコンソール アプリケーション プロジェクトでは、「[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)」のサンプルを拡張します。  基本的なリソース サービス サンプルは、WCF REST プログラミング モデルを使用してリソースを公開する方法を示しています。  基本的なリソース サービス サンプルでは、コレクション内の顧客を作成、取得、更新、および削除できるように、顧客コレクション リソースが公開されています。  基本的なリソース サービス サンプルでは、ネイティブでサポートされる XML と JSON の 2 つの受信要求形式のみが使用されます。  
  
 このフォーム ポスト サンプルのコンソール アプリケーションでは、HtmlFormProcessing ライブラリのカスタム フォーマッタが使用されるので、ユーザーはブラウザーを使用して HTML フォーム ポストから要求を送信することで顧客を作成できます。  また、このサンプルでは、サービスにポストバックされるフォームを含む HTML ページを返す操作も追加します。  この HTML ページは、事前に処理された T4 テンプレートを使用して生成されます。この T4 テンプレートは .tt ファイルと自動生成された .cs ファイルで構成されます。  開発者は、.tt ファイルを使用して変数と制御構造を含むテンプレート フォームで応答を作成できます。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] T4、「[コード生成と T4 テキスト テンプレート](http://go.microsoft.com/fwlink/?LinkId=178139)」を参照してください。  
  
#### サンプルを実行するには  
  
1.  フォーム ポスト サンプルのソリューションを開きます。  サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。  管理者として実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] アイコンを右クリックし、コンテキスト メニューの \[管理者として実行\] をクリックします。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションの FormPost プロジェクトを実行します。  
  
3.  コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  
  
4.  サンプルが実行されると、クライアントは現在のアクティビティのステータス \(顧客を追加しているのか、顧客を更新しているのか、顧客を削除しているのか、または現在の顧客の一覧をサービスから取得しているのか\) をコンソール ウィンドウに書き込みます。  
  
5.  顧客フォームの URI を参照するように求められます。  ブラウザーを開き、指定された URI を参照します。  顧客の名前と住所を入力し、**\[送信\]** ボタンをクリックします。  
  
6.  コンソール ウィンドウでサンプルの実行を続けるには、任意のキーを押します。  
  
7.  サンプルが完了すると、ブラウザーを使用して作成した顧客が最終的な顧客の一覧に追加されたことがわかります。  
  
8.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
---
title: フォーム ポスト
ms.date: 03/30/2017
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
ms.openlocfilehash: 005aba6ab8a8fcbe4f4e4f79055e04cff059f47d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503764"
---
# <a name="form-post"></a>フォーム ポスト
このサンプルでは、WCF REST プログラミング モデルを拡張して新しい受信要求形式をサポートする方法を示します。 このサンプルには、要求を HTML フォーム ポストから [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型に逆シリアル化できるフォーマッタの実装も含まれています。 また、このサンプルでは T4 テンプレートを使用して、ユーザーが WCF REST サービスにポストバックできる HTML フォームを提供する HTML ページを返します。  
  
## <a name="demonstrates"></a>使用例  
  
-   受信要求形式のサポートの拡張。  
  
-   T4 テンプレートの統合。  
  
## <a name="discussion"></a>説明  
 このサンプルは、2 つのプロジェクトで構成されます。 1 つ目のプロジェクトは、HTML フォーム ポストを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型に逆シリアル化できるカスタム要求フォーマッタを含む HtmlFormProcessing ライブラリです。 2 つ目のプロジェクトは、HtmlFormProcessing ライブラリのカスタム要求フォーマッタを使用するように基本的なリソース サービス サンプルを拡張するコンソール アプリケーションです。  
  
 HTML フォーム ポストを逆シリアル化できるカスタム フォーマッタ (HtmlFormRequestDispatchFormatter) は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] を使用して文字列から変換できる <xref:System.ServiceModel.Dispatcher.QueryStringConverter> 型と、QueryStringConverter を使用して文字列から変換できるメンバーのみを持つ <xref:System.Runtime.Serialization.DataContractAttribute> でマークされた型の両方を受け入れます。  
  
 HtmlFormProcessing ライブラリ プロジェクトには、他のカスタム要求フォーマッタを作成するために使用できる抽象基本クラス `RequestBodyDispatchFormatter` も含まれています。 `RequestBodyDispatchFormatter` から派生させると、開発者は、基本クラスで URI テンプレート パラメーターを操作のメソッド パラメーターにマップできるようにする要求本文の逆シリアル化ロジックに集中できます。 また、HtmlFormProcessing ライブラリ プロジェクトには、`HtmlFormProcessingBehavior` から派生させて既定の要求フォーマッタをカスタム要求フォーマッタに置き換える方法を示す <xref:System.ServiceModel.Description.WebHttpBehavior> クラスもあります。  
  
 このコンソール アプリケーション プロジェクトの拡張、[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプルです。 基本的なリソース サービス サンプルは、WCF REST プログラミング モデルを使用してリソースを公開する方法を示しています。 基本的なリソース サービス サンプルでは、コレクション内の顧客を作成、取得、更新、および削除できるように、顧客コレクション リソースが公開されています。 基本的なリソース サービス サンプルでは、ネイティブでサポートされる XML と JSON の 2 つの受信要求形式のみが使用されます。  
  
 このフォーム ポスト サンプルのコンソール アプリケーションでは、HtmlFormProcessing ライブラリのカスタム フォーマッタが使用されるので、ユーザーはブラウザーを使用して HTML フォーム ポストから要求を送信することで顧客を作成できます。 また、このサンプルでは、サービスにポストバックされるフォームを含む HTML ページを返す操作も追加します。 この HTML ページは、事前に処理された T4 テンプレートを使用して生成されます。この T4 テンプレートは .tt ファイルと自動生成された .cs ファイルで構成されます。 開発者は、.tt ファイルを使用して変数と制御構造を含むテンプレート フォームで応答を作成できます。 T4 の詳細については、次を参照してください。[を使用してテキスト テンプレートで成果物を生成する](http://go.microsoft.com/fwlink/?LinkId=178139)です。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  フォーム ポスト サンプルのソリューションを開きます。 サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。 これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンをクリックしてコンテキスト メニューから [管理者として実行] を選択します。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションの FormPost プロジェクトを実行します。  
  
3.  コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  
  
4.  サンプルが実行されると、クライアントは現在のアクティビティのステータス (顧客を追加しているのか、顧客を更新しているのか、顧客を削除しているのか、または現在の顧客の一覧をサービスから取得しているのか) をコンソール ウィンドウに書き込みます。  
  
5.  顧客フォームの URI を参照するように求められます。 ブラウザーを開き、指定された URI を参照します。 クリックして、顧客のアドレスと名前を入力、**送信**ボタンをクリックします。  
  
6.  コンソール ウィンドウでサンプルの実行を続けるには、任意のキーを押します。  
  
7.  サンプルが完了すると、ブラウザーを使用して作成した顧客が最終的な顧客の一覧に追加されたことがわかります。  
  
8.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`

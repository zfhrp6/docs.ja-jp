---
title: 高度な形式選択
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: 4913d8dbf69f574aa4f329279bed0d92710512f9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="advanced-format-selection"></a>高度な形式選択
このサンプルでは、新しい送信応答形式をサポートするために Windows Communication Foundation (WCF) の REST プログラミング モデルを拡張する方法を示します。 また、このサンプルでは T4 テンプレートを使用して応答を XHTML ページとして返し、ビュースタイル プログラミング モデルの実装方法も示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルは、単純なサービスと、サービスに要求を発行するクライアント コードで構成されます。  サービスは、単一の [WebGet] 操作をサポートします。この操作には、`Message EchoListWithGet(string list);` のメソッド シグネチャがあります。  
  
 クライアントでサービスに対する要求が発行されると、`list` クエリ文字列パラメーターの項目のコンマで区切られた一覧が示され、サービスからは、XML、JSON、Atom、XHTML、または jpeg のいずれかの形式で同じ一覧が返されます。  
  
 サービスから返される応答の形式は、最初は `format` クエリ文字列パラメーターで決定され、2 回目は要求で指定された HTTP Accept ヘッダーで決定されます。 `format` クエリ文字列パラメーターの値が前に示した形式のいずれかである場合、応答はその形式で返されます。 `format` クエリ文字列が存在しない場合、サービスは要求からの Accept ヘッダー要素を反復処理し、サービスがサポートする最初のコンテンツ タイプの形式を返します。  
  
 操作の戻り値の型については注意が必要です。 操作では、型を以外の値を返すときに、WCF REST プログラミング モデルをネイティブでのみが XML と JSON 応答形式をサポート<xref:System.ServiceModel.Channels.Message>です。 ただし、戻り値の型として <xref:System.ServiceModel.Channels.Message> が使用されている場合、メッセージの内容の形式の設定は、開発者によって完全に制御されています。  
  
 このサンプルでは、<xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A> メソッド、<xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> メソッドおよび <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> メソッドを使用して、文字列の一覧を XML、JSON、および ATOM のメッセージにそれぞれシリアル化しています。 jpeg 応答形式の場合は、<xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> メソッドが使用され、画像はストリームに保存されます。 XHTML 応答の場合、<xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> が事前に処理された T4 テンプレートと共に使用されます。この T4 テンプレートは .tt ファイルと自動生成された .cs ファイルで構成されます。 開発者は、.tt ファイルを使用して変数と制御構造を含むテンプレート フォームで応答を作成できます。 T4 の詳細については、次を参照してください。[を使用してテキスト テンプレートで成果物を生成する](http://go.microsoft.com/fwlink/?LinkId=166023)です。  
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-run-this-sample"></a>このサンプルを実行するには  
  
1.  高度な形式選択サンプルのソリューションを開きます。 サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。 これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンをクリックして選択する**管理者として実行**コンテキスト メニュー。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションの AdvancedFormatSelection プロジェクトを、デバッグを行わずに実行します。 コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  
  
3.  サンプルが実行されると、クライアントは要求をサービスに送信し、応答をコンソール ウィンドウに書き込みます。 応答の形式は、XML、JSON、Atom、および XHTML のいずれかになります。  
  
4.  .jpeg 形式の応答を要求できる URI を参照するよう要求されます。 ブラウザーを開き、指定された URI を参照します。  
  
5.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>関連項目

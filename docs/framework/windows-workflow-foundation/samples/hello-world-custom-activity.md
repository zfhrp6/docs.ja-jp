---
title: Hello World カスタム アクティビティ
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: 35ae5933515b3280b0d8d95157c8dd5f40f7b320
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="hello-world-custom-activity"></a>Hello World カスタム アクティビティ
このサンプルでは、いくつかの主要機能の Windows Workflow Foundation (WF)、単純なカスタム アクティビティを作成する方法などを示します。 このサンプルで示す機能では、C# でカスタム アクティビティを作成し、`in` 引数と `out` 引数 (<xref:System.Activities.InArgument> と <xref:System.Activities.OutArgument>) を使用します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>コードでのワークフローの作成  
 このサンプルでは、C# コードを使用して、2 つのカスタム アクティビティを作成します。 どちらのカスタム アクティビティも、<xref:System.Activities.Activity%601> から直接または間接に継承して、1 つの値を返します。 非ジェネリック クラス <xref:System.Activities.Activity> から継承する代わりにジェネリックな戻り値を使用する利点は、特定のアクティビティ (<xref:System.Activities.Statements.Assign> など) が、作成されるアクティビティの一部として使用する場合に戻り値にアクセスできることです。  
  
 AppendString  
 このアクティビティは、<xref:System.Activities.Activity%601> から継承し、2 つの文字列を 1 つに連結する <xref:System.Activities.Statements.Assign> アクティビティを使用します。  
  
 Prepend String  
 このアクティビティは、<xref:System.Activities.CodeActivity%601> から直接継承し、`AppendString` アクティビティと同様の機能を作成します。この機能は、既存のアクティビティから構成されるのではなく、コードに実装されているロジックを使用します。  
  
 このプロジェクトには、次のファイルがあります。  
  
 AppendString.cs  
 複数の文字列を 1 つにするカスタム アクティビティです。 文字列を受け取りし、リテラル テキスト文字列を出力として完全なメッセージを"says hello world"に結合します。  
  
 PrependString.cs  
 このアクティビティは、定義済みの文字列を入力文字列の先頭に付けます。  
  
 Sequence1.xaml  
 `AppendString` カスタム アクティビティと `PrependString` カスタム アクティビティを使用するワークフローです。  
  
 Program.cs  
 ワークフローを実行するプログラムです。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、HelloWorld.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。
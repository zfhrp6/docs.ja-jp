---
title: "CodeActivity クラスを使用したワークフロー アクティビティの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# CodeActivity クラスを使用したワークフロー アクティビティの作成
<xref:System.Activities.CodeActivity> を継承して作成されたアクティビティは、<xref:System.Activities.CodeActivity.Execute%2A> メソッドをオーバーライドすることで強制的な基本動作を実装できます。  
  
## CodeActivityContext の使用  
 ワークフロー ランタイムの機能は、<xref:System.Activities.CodeActivityContext> 型の `context` パラメーターを使用して、<xref:System.Activities.CodeActivity.Execute%2A> メソッド内からアクセスできます。<xref:System.Activities.CodeActivityContext> を介して、以下のような機能を使用できます。  
  
-   変数と引数の値を取得および設定。  
  
-   <xref:System.Activities.CodeActivityContext.Track%2A> を使用したカスタムの追跡機能。  
  
-   <xref:System.Activities.CodeActivityContext.GetProperty%2A> を使用したアクティビティの実行プロパティへのアクセス。  
  
#### CodeActivity を継承するカスタム アクティビティを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。  
  
2.  **\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順に選択します。**\[プロジェクトの種類\]** ウィンドウの **\[Visual C\#\]** の下にある **\[ワークフロー 4.0\]** を選択し、**v2010 ノード**を選択します。**\[テンプレート\]** ウィンドウで **\[アクティビティ ライブラリ\]** をクリックします。新しいプロジェクトに HelloActivity という名前を付けます。  
  
3.  HelloActivity プロジェクトの Activity1.xaml を右クリックし、**\[削除\]** をクリックします。  
  
4.  HelloActivity プロジェクトを右クリックして、**\[追加\]**、**\[クラス\]** の順に選択します。新しいクラスに HelloActivity.cs という名前を付けます。  
  
5.  HelloActivity.cs ファイルで、次の `using` ディレクティブを追加します。  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  クラス宣言に基本クラスを追加して、新しいクラスを <xref:System.Activities.CodeActivity> から継承します。  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  <xref:System.Activities.CodeActivity.Execute%2A> メソッドを追加して、このクラスに機能を追加します。  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <xref:System.Activities.CodeActivityContext> を使用して追跡レコードを作成します。  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
  
    ```
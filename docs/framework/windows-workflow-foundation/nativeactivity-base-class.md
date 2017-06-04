---
title: "NativeActivity の基本クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# NativeActivity の基本クラス
<xref:System.Activities.NativeActivity> はプロテクト コンストラクターを持つ抽象クラスです。<xref:System.Activities.CodeActivity> と同様に、<xref:System.Activities.NativeActivity> は、<xref:System.Activities.NativeActivity.Execute%2A> メソッドを実装して、強制的な動作を記述するときに使用します。<xref:System.Activities.CodeActivity> とは異なり、<xref:System.Activities.NativeActivity> からは、<xref:System.Activities.NativeActivity.Execute%2A> メソッドに渡される <xref:System.Activities.NativeActivityContext> オブジェクトを介して、ワークフロー ランタイムの公開されているすべての機能にアクセスできます。  
  
## NativeActivityContext の使用  
 ワークフロー ランタイムの機能には、<xref:System.Activities.NativeActivityContext> 型の `context` パラメーターを使用して、<xref:System.Activities.NativeActivity.Execute%2A> メソッド内からアクセスできます。<xref:System.Activities.NativeActivityContext> を介して、以下の機能を使用できます。  
  
-   引数と変数を取得および設定する。  
  
-   <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> を使用して子のアクティビティのスケジュールを設定する。  
  
-   <xref:System.Activities.NativeActivityContext.Abort%2A> を使用してアクティビティの実行を中止する。  
  
-   <xref:System.Activities.NativeActivityContext.CancelChild%2A> および <xref:System.Activities.NativeActivityContext.CancelChildren%2A> を使用して子の実行を取り消す。  
  
-   <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>、<xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>、および <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> などのメソッドを使用して、アクティビティのブックマークにアクセスする。  
  
-   <xref:System.Activities.CodeActivityContext.Track%2A> を使用したカスタムの追跡機能。  
  
-   <xref:System.Activities.CodeActivityContext.GetProperty%2A> および <xref:System.Activities.NativeActivityContext.GetValue%2A> を使用して、アクティビティの実行プロパティと値プロパティにアクセスする。  
  
-   <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> および <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A> を使用してアクティビティのアクションと機能のスケジュールを設定する。  
  
#### NativeActivity から継承するカスタム アクティビティを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。**\[プロジェクトの種類\]** ウィンドウの **\[Visual C\#\]** の下にある **\[ワークフロー 4.0\]** を選択し、v2010 ノードを選択します。**\[テンプレート\]** ウィンドウで **\[アクティビティ ライブラリ\]** をクリックします。新しいプロジェクトに HelloActivity という名前を付けます。  
  
3.  HelloActivity プロジェクトの Activity1.xaml を右クリックし、**\[削除\]** をクリックします。  
  
4.  HelloActivity プロジェクトを右クリックして、**\[追加\]** の **\[クラス\]** をクリックします。新しいクラスに HelloActivity.cs という名前を付けます。  
  
5.  HelloActivity.cs ファイルで、次の `using` ディレクティブを追加します。  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  クラス宣言に基本クラスを追加することにより、新しいクラスで <xref:System.Activities.NativeActivity> から継承します。  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  <xref:System.Activities.NativeActivity.Execute%2A> メソッドを追加して、このクラスに機能を追加します。  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <xref:System.Activities.NativeActivity.CacheMetadata%2A> メソッドをオーバーライドして適切な Add メソッドを呼び出し、カスタム アクティビティの変数、引数、子およびデリゲートについてワークフロー ランタイムに通知します。詳細については、<xref:System.Activities.NativeActivityMetadata> クラスのトピックを参照してください。  
  
9. <xref:System.Activities.NativeActivityContext> オブジェクトを使用してブックマークをスケジュールします。ブックマークを作成、スケジュール、および再開する方法の詳細については、「<xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>」を参照してください。  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
  
    ```
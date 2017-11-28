---
title: "実行時における DynamicActivity を使用したアクティビティの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c984d235521a86c9657630d7ace3341c68f806ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>実行時における DynamicActivity を使用したアクティビティの作成
<xref:System.Activities.DynamicActivity> は、パブリック コンストラクターを持つ、具体的なシール クラスです。 <xref:System.Activities.DynamicActivity> は、実行時にアクティビティ DOM を使用してアクティビティの機能を構築するために使用できます。  
  
## <a name="dynamicactivity-features"></a>DynamicActivity の機能  
 <xref:System.Activities.DynamicActivity> は、実行プロパティ、引数、変数にアクセスできますが、子アクティビティのスケジュール設定や追跡などのランタイム サービスにはアクセスできません。  
  
 最上位のプロパティは、ワークフローの <xref:System.Activities.Argument> オブジェクトを使用して設定できます。 命令型コードでは、これらの引数は新しい型で CLR プロパティを使用して作成されます。 XAML では `x:Class` タグおよび `x:Member` タグを使用して、これらの引数が宣言されます。  
  
 <xref:System.Activities.DynamicActivity> を使用して構築されたアクティビティは、<xref:System.ComponentModel.ICustomTypeDescriptor> を使用してデザイナーとやり取りします。 デザイナーで作成されたアクティビティは、次の手順に示すように、<xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> を使用して動的に読み込むことができます。  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>命令型コードを使用して実行時にアクティビティを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。  
  
2.  選択**ファイル**、**新しい**、**プロジェクト**です。 選択**Workflow 4.0**  **Visual c#**で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。 選択**シーケンシャル ワークフロー コンソール アプリケーション**で、**テンプレート**ウィンドウです。 新しいプロジェクトに DynamicActivitySample という名前を付けます。  
  
3.  HelloActivity プロジェクトの Workflow1.xaml を右クリックし **削除**です。  
  
4.  Program.cs を開きます。 次のディレクティブをファイルの先頭に追加します。  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  1 つの `Main` アクティビティを含む <xref:System.Activities.Statements.Sequence> アクティビティを作成する次のコードで <xref:System.Activities.Statements.WriteLine> メソッドの内容を置き換え、新しい動的アクティビティの <xref:System.Activities.DynamicActivity.Implementation%2A> プロパティに割り当てます。  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  アプリケーションを実行します。 コンソール ウィンドウにテキスト"Hello World!" 表示されます。  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>XAML を使用して実行時にアクティビティを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。  
  
2.  選択**ファイル**、**新しい**、**プロジェクト**です。 選択**Workflow 4.0**  **Visual c#**で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。 選択**ワークフロー コンソール アプリケーション**で、**テンプレート**ウィンドウです。 新しいプロジェクトに DynamicActivitySample という名前を付けます。  
  
3.  HelloActivity プロジェクトの Workflow1.xaml を開きます。 クリックして、**引数**デザイナーの下部にあるオプション。 `In` 型の `TextToWrite` という新しい `String` 引数を作成します。  
  
4.  ドラッグ、 **WriteLine**からアクティビティを**プリミティブ**デザイナー画面には、ツールボックスのセクションです。 値を割り当てる`TextToWrite`を**テキスト**アクティビティのプロパティです。  
  
5.  Program.cs を開きます。 次のディレクティブをファイルの先頭に追加します。  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  `Main` メソッドの内容を次のコードに置き換えます。  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  アプリケーションを実行します。 コンソール ウィンドウにテキスト"Hello World!" 表示されます。  
  
8.  Workflow1.xaml ファイルを右クリックし、**ソリューション エクスプ ローラー**選択**コードの表示**です。 アクティビティ クラスが `x:Class` を使用して作成され、プロパティが `x:Property` を使用して作成されています。  
  
## <a name="see-also"></a>関連項目  
 [命令型コードを使用してワークフロー、アクティビティ、および式を作成する方法](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [DynamicActivity の作成](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)

---
title: "方法: カスタム アクティビティ テンプレートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 方法: カスタム アクティビティ テンプレートを作成する
カスタム複合アクティビティなどのアクティビティの構成のカスタマイズには、カスタム アクティビティ テンプレートが使用されるため、手動で各アクティビティを個別に作成し、そのプロパティおよびその他の設定を構成する必要はありません。このようなカスタム テンプレートは、[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 上の **\[ツールボックス\]** または再ホストされたデザイナーから利用できるようにすることが可能です。ユーザーは、ここから構成済みのデザイン サーフェイスにカスタム テンプレートをドラッグできます。[!INCLUDE[wfd2](../../../includes/wfd2-md.md)] には以下のようなテンプレートの例が梱包されます: [SendAndReceiveReply テンプレート デザイナー](../Topic/SendAndReceiveReply%20Template%20Designer.md) および [メッセージング アクティビティ デザイナー](../Topic/Messaging%20Activity%20Designers.md) の [ReceiveAndSendReply テンプレート デザイナー](../Topic/ReceiveAndSendReply%20Template%20Designer.md) カテゴリ。  
  
 このトピックの最初の手順では、**Delay** アクティビティのカスタム アクティビティ テンプレートを作成する方法について説明し、2 番目の手順では、[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]でカスタム アクティビティ テンプレートを利用できるようにしてカスタム テンプレートが機能することを確認する方法について簡単に説明します。  
  
 カスタム アクティビティ テンプレートに <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装する必要があります。このインターフェイスには単一の <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> メソッドがあり、このメソッドを使用して、テンプレートで使用されるアクティビティ インスタンスを作成および構成できます。  
  
### Delay アクティビティのテンプレートを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[プロジェクトの種類\]** ペインで、プログラミング言語の設定に応じて、**\[Visual C\#\]** プロジェクトまたは **\[Visual Basic\]** グループから **\[ワークフロー\]** を選択します。  
  
4.  **\[テンプレート\]** ペインで **\[アクティビティ ライブラリ\]** をクリックします。  
  
5.  **\[名前\]** ボックスに、「`DelayActivityTemplate`」と入力します。  
  
6.  **\[場所\]** テキスト ボックスと **\[ソリューション名\]** テキスト ボックスの既定の設定を受け入れ、**\[OK\]** をクリックします。  
  
7.  **ソリューション エクスプローラー**で、DelayActivityTemplate プロジェクトの \[参照設定\] ディレクトリを右クリックし、**\[参照の追加\]** をクリックして **\[参照の追加\]** ダイアログ ボックスを開きます。  
  
8.  **\[.NET\]** タブに移動し、左側の **\[コンポーネント名\]** 列から **\[PresentationFramework\]** を選択します。**\[OK\]** をクリックして PresentationFramework.dll ファイルへの参照を追加します。  
  
9. この手順を繰り返して、System.Activities.Presentation.dll ファイルと WindowsBase.dll ファイルへの参照を追加します。  
  
10. **ソリューション エクスプローラー**で、DelayActivityTemplate プロジェクトを右クリックして **\[追加\]** をポイントし、**\[新しい項目\]** をクリックして **\[新しい項目の追加\]** ダイアログ ボックスを開きます。  
  
11. **\[クラス\]** テンプレートを選択し、"MyDelayTemplate" という名前を付けて、**\[OK\]** をクリックします。  
  
12. MyDelayTemplate.cs ファイルを開き、次のステートメントを追加します。  
  
    ```  
  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
  
    ```  
  
13. 次のコードを使用して、`MyDelayActivity` クラスを持つ <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装します。これにより、10 秒間の遅延が構成されます。  
  
    ```  
  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
  
    ```  
  
14. **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックして、DelayActivityTemplate.dll ファイルを生成します。  
  
### ワークフロー デザイナーでテンプレートを利用できるようにするには  
  
1.  **ソリューション エクスプローラー**で、DelayActivityTemplate ソリューションを右クリックして **\[追加\]** をポイントし、**\[新しいプロジェクト\]** をクリックして **\[新しいプロジェクトの追加\]** ダイアログ ボックスを開きます。  
  
2.  **\[ワークフロー コンソール アプリケーション\]** テンプレートを選択し、"`CustomActivityTemplateApp`" という名前を付けて、**\[OK\]** をクリックします。  
  
3.  **ソリューション エクスプローラー**で、CustomActivityTemplateApp プロジェクトの \[参照設定\] ディレクトリを右クリックし、**\[参照の追加\]** をクリックして **\[参照の追加\]** ダイアログ ボックスを開きます。  
  
4.  **\[プロジェクト\]** タブに移動し、左側の **\[プロジェクト名\]** 列から **\[DelayActivityTemplate\]** を選択します。**\[OK\]** をクリックして、最初の手順で作成した DelayActivityTemplate.dll ファイルへの参照を追加します。  
  
5.  **ソリューション エクスプローラー**で CustomActivityTemplateApp プロジェクトを右クリックし、**\[ビルド\]** をクリックしてアプリケーションをコンパイルします。  
  
6.  **ソリューション エクスプローラー**で CustomActivityTemplateApp プロジェクトを右クリックして **\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
7.  **\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、cmd.exe ウィンドウから要求されたら任意のキーを押して続行します。  
  
8.  Workflow1.xaml ファイルを開き、**\[ツールボックス\]** を開きます。  
  
9. **DelayActivityTemplate** カテゴリの **MyDelayActivity** テンプレートを見つけます。デザイン サーフェイスにドラッグします。**\[プロパティ\]** ウィンドウで、`Duration` プロパティが 10 秒に設定されていることを確認します。  
  
## 使用例  
 MyDelayActivity.cs ファイルには次のコードが含まれます。  
  
```  
  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
//Namespaces added  
using System.Activities;  
using System.Activities.Statements;  
using System.Activities.Presentation;  
using System.Windows;  
  
namespace DelayActivityTemplate  
{  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
}  
  
```  
  
## 参照  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>   
 [ワークフロー デザイン操作のカスタマイズ](../../../docs/framework/windows-workflow-foundation//customizing-the-workflow-design-experience.md)
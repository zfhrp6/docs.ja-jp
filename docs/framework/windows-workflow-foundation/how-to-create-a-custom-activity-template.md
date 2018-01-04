---
title: "方法: カスタム アクティビティ テンプレートを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 772ad2a7ea56001bf3ecba089e62d6bc0f59e5ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-activity-template"></a>方法: カスタム アクティビティ テンプレートを作成する
カスタム複合アクティビティなどのアクティビティの構成のカスタマイズには、カスタム アクティビティ テンプレートが使用されるため、手動で各アクティビティを個別に作成し、そのプロパティおよびその他の設定を構成する必要はありません。 これらのカスタム テンプレートで使用できる、**ツールボックス**上、[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]または再ホストされたデザイナーでは、元のユーザーに画面にドラッグできる、構成済みのデザインからです。 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]このようなテンプレートの良い例が付属しています。 [SendAndReceiveReply テンプレート デザイナー](/visualstudio/workflow-designer/sendandreceivereply-template-designer)と[ReceiveAndSendReply テンプレート デザイナー](/visualstudio/workflow-designer/receiveandsendreply-template-designer)で、[メッセージング アクティビティ デザイナー](/visualstudio/workflow-designer/messaging-activity-designers)カテゴリ。  
  
 このトピックの最初の手順は、カスタム アクティビティ テンプレートを作成する方法を説明、**遅延**アクティビティと 2 番目の手順について簡単にする方法について説明で使用できるように、[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]カスタム テンプレートが機能することを確認します。  
  
 カスタム アクティビティ テンプレートに <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装する必要があります。 このインターフェイスには単一の <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> メソッドがあり、このメソッドを使用して、テンプレートで使用されるアクティビティ インスタンスを作成および構成できます。  
  
### <a name="to-create-a-template-for-the-delay-activity"></a>Delay アクティビティのテンプレートを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を起動します。  
  
2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#**プロジェクトまたは**Visual Basic**に応じてグループ化、言語の優先順位。  
  
4.  **テンプレート**ペインで、**アクティビティ ライブラリ**です。  
  
5.  **名前**ボックスに、入力`DelayActivityTemplate`です。  
  
6.  既定値を受け入れます、**場所**と**ソリューション名**テキスト ボックス、およびクリック**[ok]**です。  
  
7.  DelayActivityTemplate プロジェクトの 参照設定 ディレクトリを右クリックして**ソリューション エクスプ ローラー**選択**参照の追加**を開くには、**参照の追加** ダイアログ ボックス。  
  
8.  移動、 **.NET**タブおよび選択**PresentationFramework**から、**コンポーネント名**クリックして左列**OK**参照を追加するにはPresentationFramework.dll ファイル。  
  
9. この手順を繰り返して、System.Activities.Presentation.dll ファイルと WindowsBase.dll ファイルへの参照を追加します。  
  
10. DelayActivityTemplate プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**し**新しい項目の**を開くには、 **の新しい項目の追加** ダイアログ ボックス。  
  
11. 選択、**クラス**テンプレート、MyDelayTemplate、という名前をクリック**OK**です。  
  
12. MyDelayTemplate.cs ファイルを開き、次のステートメントを追加します。  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. 次のコードを使用して、<xref:System.Activities.Presentation.IActivityTemplateFactory> クラスを持つ `MyDelayActivity` を実装します。 これにより、10 秒間の遅延が構成されます。  
  
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
  
14. 選択**ソリューションのビルド**から、**ビルド**メニュー DelayActivityTemplate.dll ファイルを生成します。  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a>ワークフロー デザイナーでテンプレートを利用できるようにするには  
  
1.  DelayActivityTemplate ソリューションを右クリックして**ソリューション エクスプ ローラー**選択**追加**し**新しいプロジェクト**を開くには、 **の新しいプロジェクトの追加**  ダイアログ ボックス。  
  
2.  選択、**ワークフロー コンソール アプリケーション**テンプレート、名前を付けます`CustomActivityTemplateApp`、順にクリック**[ok]**です。  
  
3.  CustomActivityTemplateApp プロジェクトの [参照設定] ディレクトリを右クリックして**ソリューション エクスプ ローラー**選択**参照の追加**を開くには、**参照の追加**ダイアログボックスです。  
  
4.  移動して、**プロジェクト**タブおよび選択**DelayActivityTemplate**から、**プロジェクト名**クリックして左の列**OK**を追加する、最初の手順で作成した DelayActivityTemplate.dll ファイルへの参照します。  
  
5.  CustomActivityTemplateApp プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**ビルド**アプリケーションをコンパイルします。  
  
6.  CustomActivityTemplateApp プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。  
  
7.  選択**デバッグなしで開始**から、**デバッグ**メニューとキーを押して任意のキーを cmd.exe ウィンドウから入力を求められたらを続行します。  
  
8.  Workflow1.xaml ファイルを開き、開き、**ツールボックス**です。  
  
9. 検索、 **MyDelayActivity**でテンプレート、 **DelayActivityTemplate**カテゴリ。 デザイン サーフェイスにドラッグします。 ことを確認、**プロパティ**ウィンドウを`Duration`プロパティが 10 秒に設定されています。  
  
## <a name="example"></a>例  
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
  
## <a name="see-also"></a>参照  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [ワークフロー デザイン操作のカスタマイズ](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)

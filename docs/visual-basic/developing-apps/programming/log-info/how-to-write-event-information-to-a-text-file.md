---
title: "方法: イベント情報をテキスト ファイルに書き込む (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files, writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2701f634332acdfaa81a6bf4e1d1309968366d7f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>方法: イベント情報をテキスト ファイルに書き込む (Visual Basic)
`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。 この例では、`My.Application.Log.WriteEntry` メソッドを使ってトレース情報をログ ファイルに記録する方法を示します。  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>ファイル ログ リスナーを追加および構成するには  
  
1.  **ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]**を選択します。  
  
     \- または  
  
     app.config ファイルがない場合は、次の操作を行います。  
  
    1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
    2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。  
  
    3.  **[追加]**をクリックします。  
  
2.  アプリケーション構成ファイルで `<listeners>` セクションを見つけます。  
  
     \<listeners> セクションは、最上位の \<configuration> セクションに入れ子になった \<system.diagnostics> セクションにさらに入れ子になっている、名前属性が "DefaultSource" の \<source> セクションにあります。  
  
3.  その `<listeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  最上位の `<configuration>` セクションに入れ子になっている `<system.diagnostics>` セクションで、`<sharedListeners>` セクションを見つけます。  
  
5.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     `customlocation` 属性の値をログ ディレクトリに変更します。  
  
    > [!NOTE]
    >  リスナー プロパティの値を設定するには、プロパティと同じ名前ですべてが英小文字の属性を使います。 たとえば、`location` 属性と `customlocation` 属性では、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> プロパティと <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> プロパティの値が設定されます。  
  
### <a name="to-write-event-information-to-the-file-log"></a>イベント情報をファイル ログに書き込むには  
  
-   ファイル ログに情報を書き込むには、`My.Application.Log.WriteEntry` メソッドまたは `My.Application.Log.WriteException` メソッドを使います。 詳しくは、「[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)」および「[方法: 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」をご覧ください。  
  
     アセンブリに対してファイル ログ リスナーを設定すると、リスナーはそのアセンブリから `My.Application.Log` によって書き込まれたすべてのメッセージを受け取ります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)

---
title: "Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Application object, developing applications"
  - "rapid application development (RAD), My.Application"
  - "rapid application development (RAD), My.Computer"
  - "rapid application development (RAD), My.User"
  - "My.Computer object, developing applications"
  - "My.User object, developing applications"
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

情報や一般的に使用される機能へのアクセスを提供する 3 つの中心的な `My` オブジェクトとして、`My.Application` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>\)、`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\)、および `My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\) があります。  これらのオブジェクトを使用すると、現在のアプリケーションに関する情報、アプリケーションがインストールされているコンピューターに関する情報、またはアプリケーションの現在のユーザーに関する情報にそれぞれアクセスできます。  
  
## My.Application、My.Computer、My.User  
 次の例は、`My` を使用して情報を取得する方法を具体的に示しています。  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 情報を取得できるだけでなく、これらの 3 つのオブジェクトを介して公開されるメンバーは、そのオブジェクトに関連するメソッドを実行することもできます。  たとえば、`My.Computer` を利用すると、ファイルの操作やレジストリの更新を行うさまざまなメソッドにアクセスできます。  
  
 `My` には、ファイル、ディレクトリ、およびドライブを操作するさまざまなメソッドとプロパティが含まれており、これを使用するとファイル I\/O が大幅に簡単かつ高速になります。  <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトを使用すると、区切り記号で区切られたフィールドや固定幅のフィールドを持つ大きな構造化ファイルからデータを読み取ることができます。  この例では、`reader` という `TextFieldParser` を開き、それを使用して `C:\TestFolder1\test1.txt` から読み込みを行います。  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application` を使用すると、アプリケーションのカルチャを変更できます。  次の例は、このメソッドを呼び出す方法を具体的に示しています。  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
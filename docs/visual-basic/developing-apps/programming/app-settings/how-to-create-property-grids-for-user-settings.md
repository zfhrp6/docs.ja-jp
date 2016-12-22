---
title: "How to: Create Property Grids for User Settings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings object, creating property grids for user settings"
  - "user settings, creating property grids"
  - "property grids, creating for user settings"
  - "property grids"
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create Property Grids for User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

<xref:System.Windows.Forms.PropertyGrid> コントロールに対して、`My.Settings` オブジェクトのユーザー設定プロパティを設定すると、ユーザー設定のためのプロパティ グリッドを作成できます。  
  
> [!NOTE]
>  この例が動作するためには、アプリケーションでユーザー設定が構成されている必要があります。  詳細については、「[アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)」を参照してください。  
  
 `My.Settings` オブジェクトでは、各設定がプロパティとして公開されています。  プロパティの名前は設定の名前と同じで、プロパティの型は設定の型と同じです。  プロパティが読み取り専用かどうかは、設定の**スコープ**で決定されます。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み書き可能です。  詳細については、「[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
> [!NOTE]
>  アプリケーションスコープの設定値を実行時に変更または保存することはできません。  アプリケーションスコープの設定を変更するには、アプリケーションを作成するときに**プロジェクト デザイナー**を使用して変更するか、またはアプリケーションの構成ファイルを編集するかのいずれかの方法のみが使用できます。  詳細については、「[アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)」を参照してください。  
  
 この例では、<xref:System.Windows.Forms.PropertyGrid> コントロールを使用して、`My.Settings` オブジェクトのユーザー設定プロパティにアクセスします。  既定では、<xref:System.Windows.Forms.PropertyGrid> には `My.Settings` オブジェクトのすべてのプロパティが表示されます。  一方、ユーザー設定プロパティは <xref:System.Configuration.UserScopedSettingAttribute> 属性を持ちます。  この例では、<xref:System.Windows.Forms.PropertyGrid> の <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> プロパティを <xref:System.Configuration.UserScopedSettingAttribute> に設定して、ユーザー設定プロパティのみを表示します。  
  
### ユーザー設定のプロパティ グリッドを追加するには  
  
1.  アプリケーションのデザイン サーフェイス \(ここでは  `Form1` とする\) に対して、**ツールボックス**から **PropertyGrid** コントロールを追加します。  
  
     プロパティグリッド コントロールの既定の名前は `PropertyGrid1` です。  
  
2.  `Form1` のデザイン サーフェイスをダブルクリックし、フォーム読み込みのイベント ハンドラーのコードを開きます。  
  
3.  `My.Settings` オブジェクトを、プロパティ グリッド用に選択されたオブジェクトとして設定します。  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  ユーザー設定のみを表示するようにプロパティ グリッドを構成します。  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  アプリケーション スコープの設定のみを表示するには、<xref:System.Configuration.UserScopedSettingAttribute>の代わりに <xref:System.Configuration.ApplicationScopedSettingAttribute> の属性を使用します。  
  
## 信頼性の高いプログラミング  
 アプリケーションがユーザー設定を保存するのは、アプリケーションが終了するときです。  設定をすぐに保存するには、`My.Settings.Save` メソッドを呼び出します。  詳細については、「[How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)」を参照してください。  
  
## 参照  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Change User Settings in Visual Basic](../Topic/How%20to:%20Change%20User%20Settings%20in%20Visual%20Basic.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)
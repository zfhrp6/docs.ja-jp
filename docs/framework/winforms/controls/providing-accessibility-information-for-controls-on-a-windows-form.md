---
title: "Windows フォーム上のコントロールのユーザー補助情報の提供 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows フォーム コントロール、アクセシビリティ"
  - "コントロール [Windows フォーム], ユーザー補助"
  - "アクセシビリティ、Windows フォーム コントロール"
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows フォーム上のコントロールのユーザー補助情報の提供
ユーザー補助機能は専用のプログラムおよびデバイスで、障害を持つユーザーがコンピューターをより効果的に使用するよう助けます。 たとえば、視覚障碍者のためのスクリーン リーダーや、マウスまたはキーボードではなく音声コマンド入力を利用するユーザーのための音声入力ユーティリティがあります。 これらのユーザー補助機能は、Windows フォーム コントロールによって公開されているアクセシビリティのプロパティと連携します。 これらのプロパティとは:  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## AccessibilityObject プロパティ  
 この読み取り専用プロパティには [AccessibleObject クラス](frlrfSystemWindowsFormsAccessibleObjectClassTopic) インスタンスが含まれます。**AccessibleObject** は、コントロールの説明、画面上の位置、ナビゲーション能力、および値に関する情報を提供する <xref:Accessibility.IAccessible> インターフェイスを実装します。 デザイナーは、コントロールがフォームに追加されたときにこの値を設定します。  
  
## AccessibleDefaultActionDescription プロパティ  
 この文字列は、コントロールの操作について説明します。 \[プロパティ\] ウィンドウには表示されず、コードでのみ設定できます。 次の例では、このプロパティをボタン コントロールに設定します。  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## AccessibleDescription プロパティ  
 この文字列はコントロールについて説明します。 これは、\[プロパティ\] ウィンドウで、または次のようにコードで設定できます。  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## AccessibleName プロパティ  
 これは、ユーザー補助機能に報告されたコントロールの名前です。 これは、\[プロパティ\] ウィンドウで、または次のようにコードで設定できます。  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## AccessibleRole プロパティ  
 このプロパティには [AccessibleRole 列挙](frlrfSystemWindowsFormsAccessibleRoleClassTopic)列挙型が含まれており、コントロールのユーザー インターフェイスの役割について説明します。 新しいコントロールは値が `Default` に設定されています。 つまり、**ボタン** コントロールは既定値では**ボタン**として機能します。 コントロールに別の役割がある場合、このプロパティをリセットできます。 たとえば、**PictureBox** コントロールを **Chart** として使用する場合、**PictureBox** ではなく **Chart** としてユーザー補助機能が役割を報告するようにできます。 また、開発したカスタム コントロールにこのプロパティを指定することもできます。 このプロパティは、\[プロパティ\] ウィンドウで、または次のようにコードで設定できます。  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## 参照  
 <xref:System.Windows.Forms.AccessibleObject>   
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.AccessibleRole>
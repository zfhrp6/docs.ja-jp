---
title: "Customizing Which Objects are Available in My (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Customizing Which Objects are Available in My (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックでは、プロジェクトの `_MYTYPE` 条件付きコンパイル定数を設定することによって、有効にする `My` オブジェクトを制御する方法を説明します。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 統合開発環境 \(IDE: Integrated Development Environment\) では、プロジェクトの `_MYTYPE` 条件付きコンパイル定数とプロジェクトの種類が対応付けられています。  
  
## 定義済みの \_MYTYPE 値  
 `_MYTYPE` 条件付きコンパイル定数を設定するには、`/define` コンパイラ オプションを使用する必要があります。  `_MYTYPE` 定数に独自の値を指定するときには、円記号と引用符のシーケンス \(\\"\) で文字列値を囲む必要があります。  たとえば、次のように指定します。  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 次の表は、いくつかのプロジェクトの種類に対して設定されている `_MYTYPE` 条件付きコンパイル定数です。  
  
|プロジェクトの種類|\_MYTYPE 値|  
|---------------|----------------|  
|クラス ライブラリ|"Windows"|  
|コンソール アプリケーション|"Console"|  
|Web|"Web"|  
|Web コントロール ライブラリ|"WebControl"|  
|Windows アプリケーション|"WindowsForms"|  
|カスタムの `Sub Main` で開始される Windows アプリケーション|"WindowsFormsWithCustomSubMain"|  
|Windows コントロール ライブラリ|"Windows"|  
|Windows サービス|"Console"|  
|空|"Empty"|  
  
> [!NOTE]
>  条件付きコンパイル文字列の比較では、`Option Compare` ステートメントの設定にかかわらず、大文字と小文字は常に区別されます。  
  
## 値に応じて決まる \_MY 系コンパイル定数  
 一方、`_MYTYPE` 条件付きコンパイル定数の値に応じて、他のいくつかの `_MY` 系コンパイル定数の値が、次のように決まります。  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|未定義|"Windows"|TRUE|  
|"Custom"|未定義|未定義|未定義|未定義|未定義|  
|"Empty"|未定義|未定義|未定義|未定義|未定義|  
|"Web"|未定義|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|未定義|"Web"|FALSE|"Web"|TRUE|  
|"Windows" または ""|"Windows"|"Windows"|未定義|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 既定では、未定義の条件付きコンパイル定数は `FALSE` に解決されます。  プロジェクトをコンパイルするときに、既定の動作をオーバーライドするように未定義の定数の値を指定できます。  
  
> [!NOTE]
>  `_MYTYPE` を "Custom" に設定すると、プロジェクトに `My` 名前空間が含まれますが、オブジェクトは含まれません。  一方、`_MYTYPE` を "Empty" に設定すると、`My` 名前空間とそのオブジェクトのいずれも含まれません。  
  
 次の表は、定義済みの `_MY` 系コンパイル定数の値の効果の説明です。  
  
|定数|説明|  
|--------|--------|  
|`_MYAPPLICATIONTYPE`|定数が "Console"、"Windows"、または "WindowsForms" の場合、`My.Application` が有効になります。<br /><br /> -   "Console" バージョンは <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> から派生され、  メンバーは "Windows" バージョンより少なくなります。<br />-   "Windows" バージョンは <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> から派生され、メンバーは "WindowsForms" バージョンより少なくなります。<br />-   `My.Application` の "WindowsForms" バージョンは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> から派生されます。  `TARGET` 定数が "winexe" と定義されている場合、クラスには `Sub Main` メソッドが含まれます。|  
|`_MYCOMPUTERTYPE`|定数が "Web" または "Windows" の場合、`My.Computer` が有効になります。<br /><br /> -   "Web" バージョンは <xref:Microsoft.VisualBasic.Devices.ServerComputer> から派生され、メンバーは "Windows" バージョンより少なくなります。<br />-   `My.Computer` の "Windows" バージョンは <xref:Microsoft.VisualBasic.Devices.Computer> から派生されます。|  
|`_MYFORMS`|定数が `TRUE` の場合、`My.Forms` が有効になります。|  
|`_MYUSERTYPE`|定数が "Web" または "Windows" の場合、`My.User` が有効になります。<br /><br /> -   `My.User` の "Web" バージョンは、現在の HTTP 要求のユーザー ID と関連付けられています。<br />-   `My.User` の "Windows" バージョンは、スレッドの現在のプリンシパルと関連付けられています。|  
|`_MYWEBSERVICES`|定数が `TRUE` の場合、`My.WebServices` が有効になります。|  
|`_MYTYPE`|定数が "Web" の場合、`My.Log`、`My.Request`、および `My.Response` が有効になります。|  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)
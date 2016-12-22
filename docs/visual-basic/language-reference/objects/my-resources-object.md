---
title: "My.Resources Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.Resources"
  - "My.Resources.MyResources.ResourceManager"
  - "My.Resources.MyResources.Culture"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Resources object"
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# My.Resources Object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

アプリケーションのリソースにアクセスするための、プロパティとクラスを提供します。  
  
## 解説  
 `My.Resources` オブジェクトを使用すると、アプリケーションのリソースへのアクセスが可能になり、アプリケーションに必要なリソースを動的に取得できるようになります。  詳細については、「[アプリケーション リソースの管理 \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)」を参照してください。  
  
 `My.Resources` オブジェクトはグローバルなリソースだけを公開します。  フォームに関連付けられたリソース ファイルへのアクセスはできません。  フォームのリソースには、フォームからアクセスする必要があります。  詳細については、「[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/ja-jp/9a96220d-a19b-4de0-9f48-01e5d82679e5)」を参照してください。  
  
 アプリケーションのカルチャ固有のリソース ファイルに、`My.Resources` オブジェクトからアクセスできます。  既定では、`My.Resources` オブジェクトは、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> プロパティのカルチャに一致するリソース ファイルからリソースを検索します。  ただし、この動作をオーバーライドして、リソースに使用するカルチャを指定することもできます。  詳細については、「[デスクトップ アプリケーションのリソース](../Topic/Resources%20in%20Desktop%20Apps.md)」を参照してください。  
  
## プロパティ  
 `My.Resources` オブジェクトのプロパティでは、アプリケーションのリソースに読み取り専用でしかアクセスできません。  リソースを追加または削除するには、**プロジェクト デザイナー** を使用します。  詳細については、「[How to: Add or Remove Resources](http://msdn.microsoft.com/ja-jp/7b77bc06-3952-4799-b029-def3f8f7f88d)」を参照してください。  **プロジェクト デザイナー**で追加されたリソースには、`My.Resources.``resourceName` を使用してアクセスできます。  
  
 また、**ソリューション エクスプローラー**からプロジェクトを選択し、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** または **\[既存項目の追加\]** をクリックすることによっても、リソース ファイルを追加または削除できます。  この方法で追加したリソースには、`My.Resources.``resourceFileName`.`resourceName` を使用してアクセスできます。  
  
 各リソースには名前、カテゴリ、値が定義され、これらのリソース設定によってプロパティが `My.Resources` オブジェクトに含まれるリソースにアクセスする方法が決まります。  **プロジェクト デザイナー**で追加されたリソースの場合は、次のようになります。  
  
-   名前はプロパティの名前  
  
-   リソース データはプロパティの値  
  
-   カテゴリはプロパティの種類  
  
|||  
|-|-|  
|\[カテゴリ\]|プロパティのデータ型|  
|**Strings**|[&#91;文字列&#93;](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**\[イメージ\]**|<xref:System.Drawing.Bitmap>|  
|**\[アイコン\]**|<xref:System.Drawing.Icon>|  
|**\[オーディオ\]**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> クラスは <xref:System.IO.Stream> クラスから派生しているため、ストリームを受け取るメソッド \(<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> メソッドなど\) で使用できます。|  
|**\[ファイル\]**|-   テキスト ファイルの場合は [String](../../../visual-basic/language-reference/data-types/string-data-type.md)。<br />-   イメージ ファイルの場合は <xref:System.Drawing.Bitmap>。<br />-   アイコン ファイルの場合は <xref:System.Drawing.Icon>。<br />-   サウンド ファイルの場合は <xref:System.IO.UnmanagedMemoryStream>。|  
|**その他**|デザイナーの **\[型\]** 列の情報によって決まります。|  
  
## Classes  
 `My.Resources` オブジェクトは各リソース ファイルを、共有プロパティを持つクラスとして公開します。  クラス名はリソース ファイルの名前と同じです。  先のセクションにあるとおり、リソース ファイルのリソースはクラスのプロパティとして公開されます。  
  
## 使用例  
 この例はアプリケーションのリソース ファイルに `Form1Title` という名前の文字列リソースにフォームのタイトルを設定します。  この例を実行するにはアプリケーションのリソース ファイルに `Form1Title` という文字列が含まれている必要があります。  詳細については、「[How to: Add or Remove Resources](http://msdn.microsoft.com/ja-jp/7b77bc06-3952-4799-b029-def3f8f7f88d)」を参照してください。  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## 使用例  
 次の例は、アプリケーションのリソース ファイルに格納された `Form1Icon` という名前のアイコンを、フォームのアイコンに設定します。  この例を実行するにはアプリケーションのリソース ファイルに `Form1Icon` という名前のアイコンが必要です。  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## 使用例  
 この例では `Form1Background` という名前のアプリケーションのリソース ファイルにあるイメージ リソースにフォームの背景イメージを設定します。  この例が動作するためにはアプリケーションのリソース ファイルに `Form1Background` という名前のイメージ リソースが含まれている必要があります。  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## 使用例  
 この例ではアプリケーションのリソース ファイルに `Form1Greeting` という名前のオーディオ リソースとして格納されているサウンドを再生します。  この例を実行するにはアプリケーションのリソース ファイルに `Form1Greeting` という名前のオーディオ リソースが含まれている必要があります。  `My.Computer.Audio.Play` メソッドは、Windows フォーム アプリケーションでのみ使用できます。  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## 使用例  
 この例ではアプリケーションの文字列リソースのフランスのカルチャのバージョンを取得します。  リソース `Message` はという名前です。  `My.Resources` オブジェクトの使用例を <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> が使用するカルチャを変更します。  
  
 この例が動作するためにはアプリケーションのリソース ファイルに `Message` という文字列が含まれている必要がありアプリケーションはそのリソース ファイルである Resources.fr\-FR.resx フランスのカルチャのバージョンが必要です。  詳細については、「[How to: Add or Remove Resources](http://msdn.microsoft.com/ja-jp/7b77bc06-3952-4799-b029-def3f8f7f88d)」を参照してください。  アプリケーションにリソース ファイルのフランスのカルチャのバージョンがない場合は`My.Resource` のオブジェクトは既定のカルチャのリソース ファイルからリソースを取得します。  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## 参照  
 [How to: Add or Remove Resources](http://msdn.microsoft.com/ja-jp/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [アプリケーション リソースの管理 \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)   
 [デスクトップ アプリケーションのリソース](../Topic/Resources%20in%20Desktop%20Apps.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/ja-jp/9a96220d-a19b-4de0-9f48-01e5d82679e5)
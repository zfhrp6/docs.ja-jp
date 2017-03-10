---
title: "FileName で指定されたファイルは、正しい XML ファイルではありません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# FileName で指定されたファイルは、正しい XML ファイルではありません
指定したファイル名は、正しい XML ファイルではありません。 XML ドキュメントの許可されている構造体とコンテンツを指定する場合、ドキュメント型定義 \(DTD\)、Microsoft XML\-Data Reduced \(XDR\) スキーマ、または XML スキーマ定義言語 \(XSD\) スキーマを使用できます。[!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort-md.md)] で XML 文法を指定する場合は、XSD スキーマをお勧めします。  
  
> [!NOTE]
>  Visual Studio の以前のバージョンにある **XML デザイナー**とは、型指定されたデータセットおよび XML スキーマのデザイナーのことです。**XML デザイナー**は、XML スキーマ ファイルの作成と編集に今も使用できます。 ただし、[!INCLUDE[vs_current_long](../../csharp/misc/includes/vs-current-long-md.md)] では、型指定されたデータセットの作成と編集用のデザイナーは、**データセット デザイナー**です。 詳細については、「[型指定されたデータセットの作成と編集](/visual-studio/data-tools/creating-and-editing-typed-datasets)」を参照してください。  
  
### このエラーを解決するには  
  
-   正しいファイル名を指定していることを確認します。  
  
-   確認する必要のある XML ファイルを **XML デザイナー**に読み込んで、指定したファイルに正しい XML が含まれていることを確認します。**\[XML\]** メニューで、**\[XML の整合性チェック\]** をクリックします。 エラーは **\[タスク一覧\]** に表示されます。  
  
-   XML ファイルに関連付けられた XML スキーマがある場合は、定義された構造体にその要素が出現し、個々の要素のコンテンツがスキーマで指定された宣言されたデータ型に準拠していることを確認します。  
  
## 参照  
 <xref:System.Xml>   
 [方法 : ファイル パスを解析する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
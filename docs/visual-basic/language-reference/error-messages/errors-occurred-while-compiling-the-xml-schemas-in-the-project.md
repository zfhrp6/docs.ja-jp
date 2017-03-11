---
title: "Errors occurred while compiling the XML schemas in the project | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36810"
  - "vbc36810"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36810"
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Errors occurred while compiling the XML schemas in the project
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました。このエラーのため、XML の IntelliSense は利用できません。  
  
 プロジェクトに組み込まれている XML スキーマ定義 \(XSD: XML Schema Definition\) スキーマにエラーがあります。  このエラーは、既存の XSD スキーマ セットと競合する XSD スキーマ \(.xsd\) ファイルをプロジェクトに追加すると発生します。  
  
 **エラー ID:** BC36810  
  
### このエラーを解決するには  
  
-   **\[エラー一覧\]** ウィンドウに表示されているこの警告をダブルクリックします。  XSD ファイル内で警告の原因になっている場所が示されます。  XSD スキーマのエラーを修正します。  
  
-   すべての必要な XSD スキーマ \(.xsd\) ファイルをプロジェクトに組み込みます。  必要に応じて、**\[プロジェクト\]** メニューの **\[すべてのファイルを表示\]** をクリックして、**ソリューション エクスプローラー** で .xsd ファイルを表示します。  プロジェクトに .xsd ファイルを組み込むために、対象のファイルを右クリックして **\[プロジェクトに含める\]** をクリックします。  
  
-   XML to Schema ウィザードを使用している場合は、このエラーは、同じソースから複数回スキーマを推論すると発生することがあります。  このような場合は、プロジェクトから既存の XSD スキーマ ファイルを削除し、新しい XML to Schema 項目テンプレートを追加してから、適用可能なすべての XML ソースを XML to Schema ウィザードに指定できます。  
  
-   XSD スキーマのエラーが示されない場合は、XML コンパイラに渡されている情報が不十分で詳細なエラー メッセージを表示できない可能性があります。  プロジェクトに組み込まれている .xsd ファイルの XML 名前空間が、Visual Studio で XML スキーマ セットに指定されている XML 名前空間と一致していることを確認できれば、詳細なエラー情報を取得できる場合があります。  
  
## 参照  
 [\[エラー一覧\] ウィンドウ](/visual-studio/ide/reference/error-list-window)   
 [XML IntelliSense in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
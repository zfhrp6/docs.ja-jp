---
title: "Expression of type &lt;type&gt; is not queryable | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36593"
  - "vbc36593"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36593"
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expression of type &lt;type&gt; is not queryable
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

型 \<type\> の式はクエリ不可能です。LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないことを確認してください。  
  
 クエリ可能型は、<xref:System.Linq>、<xref:System.Data.Linq>、<xref:System.Xml.Linq> の各名前空間で定義されています。  LINQ クエリを実行するには、そのいずれかの名前空間をインポートする必要があります。  
  
 <xref:System.Linq> 名前空間を使用すれば、LINQ によってコレクションや配列などのオブジェクトにクエリを実行することが可能になります。  
  
 <xref:System.Data.Linq> 名前空間を使用すれば、LINQ によって ADO.NET のデータセットや SQL Server のデータベースにクエリを実行することが可能になります。  
  
 <xref:System.Xml.Linq> 名前空間を使用すれば、LINQ によって XML にクエリを実行することと、Visual Basic の XML 機能を使用することが可能になります。  
  
 **エラー ID:** BC36593  
  
### このエラーを解決するには  
  
1.  <xref:System.Linq>、<xref:System.Data.Linq>、<xref:System.Xml.Linq> のいずれかの名前空間の `Import` ステートメントをコード ファイルに追加します。  プロジェクト デザイナーの **\[参照設定\]** ページ \(**\[My Project\]**\) を使用して、プロジェクトの名前空間をインポートすることもできます。  
  
2.  クエリのソースとして指定した型がクエリ可能型であることを確認します。  つまり、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装した型です。  
  
## 参照  
 <xref:System.Linq>   
 <xref:System.Data.Linq>   
 <xref:System.Xml.Linq>   
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/References%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)
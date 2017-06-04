---
title: "XSLT 拡張オブジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XSLT 拡張オブジェクト
拡張オブジェクトは、スタイル シートの機能を拡張する場合に使用します。  拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList> クラスによって維持されます。  
  
 埋め込みスクリプトではなく、拡張オブジェクトを使用する利点を次に示します。  
  
-   クラスをより効果的にカプセル化および再利用できます。  
  
-   スタイル シートを小さくすることができ、管理が簡単になります。  
  
 XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトに追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。  その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出すには、FullTrust アクセス許可セットが必要です。  詳細については、「[Code Access Security](http://msdn.microsoft.com/ja-jp/23a20143-241d-4fe5-9d9f-3933fd594c03)」および「[NIB: Named Permission Sets](http://msdn.microsoft.com/ja-jp/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)」を参照してください。  
  
 拡張オブジェクトが返すデータ型は、4 つの基本 XPath データ型である `number`、`string`、`Boolean`、および `node set` のうちのいずれかになります。  
  
 現在、`params` キーワードを使用して定義されるメソッド \(不特定数のパラメーターを渡すことができる\) は、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでサポートされていません。  `params` キーワードを使用して定義されたメソッドを使用する XSLT スタイル シートは、正しく動作しません。  詳細については、「[params](../Topic/params%20\(C%23%20Reference\).md)」を参照してください。  
  
### XSLT 拡張オブジェクトを使用するために必要な処理  
  
1.  <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して拡張オブジェクトを追加します。  
  
2.  スタイル シートから拡張オブジェクトを呼び出します。  
  
3.  <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。  
  
## 参照  
 [XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations.md)   
 [XSLT のセキュリティに関する考慮事項](../../../../docs/standard/data/xml/xslt-security-considerations.md)
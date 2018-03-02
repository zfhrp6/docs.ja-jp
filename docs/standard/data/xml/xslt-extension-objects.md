---
title: "XSLT 拡張オブジェクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 18106b74c19ffdfc33176a12bec07daf2b19b17e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-extension-objects"></a>XSLT 拡張オブジェクト
拡張オブジェクトは、スタイル シートの機能を拡張する場合に使用します。 拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList> クラスによって維持されます。  
  
 埋め込みスクリプトではなく、拡張オブジェクトを使用する利点を次に示します。  
  
-   クラスをより効果的にカプセル化および再利用できます。  
  
-   スタイル シートを小さくすることができ、管理が簡単になります。  
  
 XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトに追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。 その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出すには、FullTrust アクセス許可セットが必要です。 詳細については、「[コード アクセス セキュリティ](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)」と [NIB: 名前付きアクセス許可セット](http://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)に関するページを参照してください。  
  
 拡張オブジェクトが返すデータ型は、4 つの基本 XPath データ型である `number`、`string`、`Boolean`、および `node set` のうちのいずれかになります。  
  
 現在、`params` キーワードを使用して定義されるメソッド (不特定数のパラメーターを渡すことができる) は、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでサポートされていません。 `params` キーワードを使用して定義されたメソッドを使用する XSLT スタイル シートは、正しく動作しません。 詳細については、[params](~/docs/csharp/language-reference/keywords/params.md) に関するページを参照してください。  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT 拡張オブジェクトを使用するために必要な処理  
  
1.  <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して拡張オブジェクトを追加します。  
  
2.  スタイル シートから拡張オブジェクトを呼び出します。  
  
3.  <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。  
  
## <a name="see-also"></a>参照  
 [XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [XSLT のセキュリティに関する考慮事項](../../../../docs/standard/data/xml/xslt-security-considerations.md)

---
title: "XSLT 変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 92d0688b86e6a95af46e09c21c1a8b3cdf66efc3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-transformations"></a>XSLT 変換
XSLT (Extensible Stylesheet Language Transformation) を使用すれば、ソース XML ドキュメントの内容を、形式や構造が異なる別のドキュメントに変換できます。 たとえば、XSLT を使用して、XML を Web サイトで使われる HTML に変換したり、アプリケーションが必要とするフィールドだけが含まれたドキュメントに変換したりできます。 この変換処理の仕様は、[W3C 勧告『XSL Transformations (XSLT) Version 1.0』](http://go.microsoft.com/fwlink/?LinkID=49919)で規定されています。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスは .NET Framework の XSLT プロセッサです。 <xref:System.Xml.Xsl.XslCompiledTransform> クラスは、W3C 勧告『XSLT 1.0』をサポートしています。  
  
> [!NOTE]
>  .NET Framework Version 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。 <xref:System.Xml.Xsl.XslCompiledTransform> クラスが XSLT エンジンの新しい実装です。 このクラスは、パフォーマンスが向上しており、新しいセキュリティ機能を備えています。 XSLT アプリケーションの作成には <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用することが推奨されています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスの使用方法について説明します。  
  
 [XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <xref:System.Xml.Xsl.XslTransform> クラスからコードを移行する方法について説明します。  
  
 [XSLT コンパイラ (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 XSLT コンパイラの使用方法について説明します。  
  
 [XslTransform クラスを使用した XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <xref:System.Xml.Xsl.XslTransform> クラスの使用方法について説明します。  
  
 **注** .NET Framework 2.0 リリースでは <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。  
  
## <a name="reference"></a>参照  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>関連項目  
 [XML ドキュメントと XML データ](../../../../docs/standard/data/xml/index.md)

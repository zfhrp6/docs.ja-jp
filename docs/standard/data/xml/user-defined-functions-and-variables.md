---
title: "ユーザー定義の関数と変数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b6870861541a063c56f83dcb286d21a5a970d1b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="user-defined-functions-and-variables"></a>ユーザー定義の関数と変数
<xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> データの操作に使用されるメソッドのセットを提供します。 XPath クエリ式で使用する拡張関数および変数を実装することで、標準の XPath 関数を補完できます。 <xref:System.Xml.XPath.XPathExpression.SetContext%2A> メソッドは、<xref:System.Xml.Xsl.XsltContext> から派生した、ユーザー定義のコンテキストを受け取ることができます。 ユーザー定義の関数は、カスタム コンテキストで解決されます。  
  
 拡張関数および変数は、XML インジェクション攻撃を防止するのに役立ちます。 このようなシナリオでは、処理命令と連結された生の入力としてではなく、ユーザー入力がカスタム変数に割り当てられ、拡張関数で処理されます。 拡張関数および変数にユーザー入力が含まれて、設計者が意図したように、XML データに対してだけ機能します。  
  
 拡張関数および変数を使用するには、カスタム クラス <xref:System.Xml.Xsl.XsltContext> を、拡張関数および変数をサポートする <xref:System.Xml.Xsl.IXsltContextFunction> インターフェイスおよび <xref:System.Xml.Xsl.IXsltContextVariable> インターフェイスと共に実装します。 <xref:System.Xml.XPath.XPathExpression> は、ユーザー入力をその <xref:System.Xml.Xsl.XsltArgumentList> と共にカスタム <xref:System.Xml.Xsl.XsltContext> に追加します。  
  
 <xref:System.Xml.XPath.XPathExpression> は、式で識別されるノードを見つけて処理するのに <xref:System.Xml.XPath.XPathNavigator> が使用する、コンパイル済みクエリを表します。  
  
 <xref:System.Xml.Xsl.XsltContext> から派生したカスタム コンテキスト クラスの実装を次の例に示します。 コード コメントは、クラスのメンバーと、カスタム関数でのそれらのメンバーの使用法を説明しています。 このコードの後に、関数および変数の実装と、それらの実装を使用するサンプル アプリケーションがあります。  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 次のコードでは <xref:System.Xml.Xsl.IXsltContextFunction> を実装します。 <xref:System.Xml.Xsl.IXsltContextFunction> を実装するクラスは、ユーザー定義の関数を解決し、実行します。 この例では、宣言 `private int CountChar(string title, char charTocount)` で識別される関数を使用します。  
  
 コード コメントでは、クラスのメンバーを示しています。  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 次のコードでは <xref:System.Xml.Xsl.IXsltContextVariable> を実装します。 このクラスは、実行時に XPath クエリ式内のユーザー定義変数への参照を解決します。 このクラスのインスタンスは、カスタム クラス <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> の、オーバーライドされた <xref:System.Xml.Xsl.XsltContext> メソッドによって作成され、返されます。  
  
 コード コメントでは、クラスのメンバーを示しています。  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 前のクラス定義がスコープ内にある次のコードでは、カスタム関数を使用して `Tasks.xml` ドキュメントの要素内の文字をカウントします。 コード コメントでは、カスタム関数をコンパイルし、それを `Tasks.xml` ドキュメントに対して実行するコードについて説明しています。  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 この例では、次の XML データを使用しています。  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]

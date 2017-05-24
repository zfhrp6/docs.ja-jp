---
title: "方法: XmlReader から XML フラグメントをストリーム出力する (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 06e2cf4b350fecf8e8310519c573ac140f05267a
ms.contentlocale: ja-jp
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>方法: XmlReader から XML フラグメントをストリーム出力する (C#)
大きな XML ファイルを処理する必要があるときに、XML ツリー全体をメモリに読み込むことができない場合があります。 このトピックでは、<xref:System.Xml.XmlReader> を使ってフラグメントをストリーム出力する方法について説明します。  
  
 <xref:System.Xml.XmlReader> を使って <xref:System.Xml.Linq.XElement> オブジェクトを読み取るための最も効果的な方法の 1 つは、カスタムの軸メソッドを独自に記述することです。 一般に軸メソッドは、このトピックの例で示すように、<xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> などのコレクションを返します。 カスタムの軸メソッドでは、<xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドを呼び出して XML フラグメントを作成した後に、`yield return` を使ってコレクションを返します。 これにより、カスタムの軸メソッドに遅延実行セマンティクスが付加されます。  
  
 <xref:System.Xml.XmlReader> オブジェクトから XML ツリーを作成する場合は、<xref:System.Xml.XmlReader> を要素に配置する必要があります。 <xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドは、要素の終了タグを読み取るまで制御を戻しません。  
  
 部分ツリーを作成する場合は、<xref:System.Xml.XmlReader> をインスタンス化し、<xref:System.Xml.Linq.XElement> ツリーに変換するノード上にリーダーを配置し、<xref:System.Xml.Linq.XElement> オブジェクトを作成します。  
  
 トピック「[方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)」には、より複雑なドキュメントをストリーム出力する方法とその例が示されています。  
  
 トピック「[方法: 大きな XML ドキュメントのストリーミング変換を実行する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)」には、LINQ to XML を使って、メモリ使用量を低く抑えながら非常に大きな XML ドキュメントを変換する例が示されています。  
  
## <a name="example"></a>例  
 次の例では、カスタムの軸メソッドを作成します。 このメソッドに対してクエリを実行するには、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを使用します。 カスタムの軸メソッド `StreamRootChildDoc` は、`Child` 要素が繰り返し出現するドキュメントを読み取るために特に設計されたメソッドです。  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
bbb  
ccc  
```  
  
 この例のソース ドキュメントは、非常に小さなドキュメントです。 ただし、何百万の `Child` 要素があっても、この例で使用されるメモリは非常に少量です。  
  
## <a name="see-also"></a>関連項目  
 [XML の解析 (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

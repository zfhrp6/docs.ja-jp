---
title: "クエリの連結の例 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 74d3dcaca686487d79a90f28faf4d9c00218f6a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-queries-example-c"></a>クエリの連結の例 (C#)
この例は前の例に基づいており、2 つのクエリ (どちらのクエリも遅延実行とレイジー評価を使用している) を連結した場合の結果について説明します。  
  
## <a name="example"></a>例  
 この例では、拡張メソッドをもう 1 つ導入します。この `AppendString` という拡張メソッドは、指定された文字列をソース コレクションのすべての文字列に追加して新しい文字列を生成します。  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 この例では、各拡張メソッドがソース コレクションのアイテムごとに 1 つずつ実行されることを確認できます。  
  
 この例からわかることは、コレクションを生成するクエリを連結しても中間コレクションは具体化されないということです。 代わりに、各アイテムが一方のレイジー メソッドから次のメソッドに渡されます。 この場合のメモリ使用量は、まず文字列の 1 つの配列を取得し、次に大文字に変換した文字列の 2 つ目の配列を作成し、最後に各文字列に感嘆符を追加した文字列の 3 つ目の配列を作成する方法と比べると、はるかに少なくなります。  
  
 このチュートリアルの次のトピックでは、中間結果の具体化について説明します。  
  
-   [中間結果の具体化 (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: クエリの連結 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)

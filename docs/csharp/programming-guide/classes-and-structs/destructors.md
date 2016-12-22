---
title: "デストラクター (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "~ [C#], デストラクター内"
  - "C# 言語, デストラクター"
  - "デストラクター [C#]"
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# デストラクター (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

デストラクターは、クラスのインスタンスを消滅させるために使用します。  
  
## 解説  
  
-   デストラクターは、構造体には定義できません。  クラスでだけ使用します。  
  
-   クラスで使用できるデストラクターは 1 つだけです。  
  
-   デストラクターを継承またはオーバーロードすることはできません。  
  
-   デストラクターを呼び出すことはできません。  デストラクターは自動的に起動されます。  
  
-   デストラクターは修飾子をとらず、パラメーターはありません。  
  
 次に示すのは、`Car` クラスに対するデストラクターの宣言の例です。  
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  
  
 デストラクターは、オブジェクトの基本クラスで <xref:System.Object.Finalize%2A> を暗黙的に呼び出します。  したがって、前のデストラクターのコードは、暗黙的に次のコードに解釈されます。  
  
```  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 つまり、最派生クラスから最低派生クラスまで、継承チェーンのすべてのインスタンスに対して、`Finalize` メソッドが再帰的に呼び出されます。  
  
> [!NOTE]
>  空のデストラクターは使用しないでください。  デストラクターがクラスに存在するときは、エントリが `Finalize` キューで作成されます。  デストラクターを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。  デストラクターが空の場合は、パフォーマンスを不必要に低下させるだけです。  
  
 デストラクターがいつ呼び出されるかはガベージ コレクターによって決定されるため、プログラマは制御できません。  ガベージ コレクターは、アプリケーションが使用していないオブジェクトをチェックします。  消滅できるオブジェクトと考えられる場合、デストラクター \(存在する場合\) を呼び出し、オブジェクトの格納に使用されているメモリをクリアします。  デストラクターは、プログラムの終了時にも呼び出されます。  
  
 <xref:System.GC.Collect%2A> を呼び出すことによって、ガベージ コレクションを強制的に行うことができます。ただし、パフォーマンスに問題が発生する可能性があるため、通常はこの処理を避けます。  
  
## デストラクターを使ったリソースの解放  
 一般に C\# では、ガベージ コレクションを使用しない言語で開発する場合ほど、メモリ管理を必要としません。  .NET Framework のガベージ コレクターが、オブジェクトに対するメモリの割り当てと解放を暗黙的に管理します。  ただし、ウィンドウ、ファイル、ネットワーク接続などのアンマネージ リソースをアプリケーションでカプセル化するときは、デストラクターを使ってこれらのリソースを解放する必要があります。  オブジェクトを消滅させることができる場合、ガベージ コレクターはそのオブジェクトの `Finalize` メソッドを実行します。  
  
## リソースの明示的な解放  
 アプリケーションで貴重な外部リソースを使用している場合は、ガベージ コレクターがオブジェクトを解放する前にリソースを明示的に解放する手段を用意することをお勧めします。  この処理を行うには、オブジェクトに対して必要なクリーンアップを実行する `Dispose` メソッドを <xref:System.IDisposable> インターフェイスから実装します。  これによって、アプリケーションのパフォーマンスを大幅に向上させることができます。  このようにリソースを明示的に制御する場合でも、デストラクターは、`Dispose` メソッドの呼び出しが失敗したときにリソースをクリーンアップするための安全装置になります。  
  
 リソースのクリーンアップの詳細については、次のトピックを参照してください。  
  
-   [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)  
  
-   [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)  
  
-   [using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)  
  
## 使用例  
 次の例では、継承のチェインを形成する 3 つのクラスを作成します。  `First` が基本クラスであり、`Second` は `First` から派生し、`Third` は `Second` から派生しています。  3 つのクラスのいずれにもデストラクターがあります。  `Main()` では、最派生クラスのインスタンスが作成されます。  プログラムを実行すると、3 つのクラスのデストラクターが、最派生クラスから最低派生クラスの順に自動的に呼び出されます。  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 <xref:System.IDisposable>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)
---
title: "loadFromContext MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MDAs (managed debugging assistants), LoadFrom context"
  - "managed debugging assistants (MDAs), LoadFrom context"
  - "LoadFrom context"
  - "LoadFromContext MDA"
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# loadFromContext MDA
`loadFromContext` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、アセンブリが `LoadFrom` コンテキストに読み込まれるとアクティブ化されます。  <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> メソッド、またはその他の類似メソッドを呼び出すと、この状況が発生することがあります。  
  
## 症状  
 一部のローダー メソッドを使用すると、アセンブリが `LoadFrom` コンテキストに読み込まれることがあります。  このコンテキストを使用すると、シリアル化、キャスト処理、依存関係解決などで、予期しない動作が発生する可能性があります。  一般的に、この問題を回避するには、アセンブリが `Load` コンテキストに読み込まれるようにしてください。  この MDA を使用しないと、アセンブリが読み込まれたコンテキストを判断するのは困難です。  
  
## 原因  
 一般に、グローバル アセンブリ キャッシュや <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName> プロパティなど、`Load` コンテキストの外部のパスからアセンブリが読み込まれると、そのアセンブリは `LoadFrom` コンテキストに読み込まれます。  
  
## 解決策  
 <xref:System.Reflection.Assembly.LoadFrom%2A> 呼び出しが必要なくなるように、アプリケーションを設定します。  これを行うのに使用するテクニックを次に示します。  
  
-   アセンブリをグローバル アセンブリ キャッシュにインストールします。  
  
-   <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> ディレクトリにアセンブリを配置します。  既定ドメインの場合、<xref:System.AppDomainSetup.ApplicationBase%2A> ディレクトリは、プロセスを開始する実行可能ファイルが含まれるディレクトリです。  アセンブリを移動することが簡単ではない場合は、新規の <xref:System.AppDomain> を作成する必要もあります。  
  
-   依存アセンブリが実行可能ファイルに関連した子ディレクトリ内にある場合は、アプリケーションの構成 \(.config\) ファイルまたは第 2 のアプリケーション ドメインに、プローブ パスを追加します。  
  
 いずれの場合も、<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> メソッドを使用するように、コードを変更できます。  
  
## ランタイムへの影響  
 この MDA は、CLR に影響ありません。  読み込み要求の結果使用されたコンテキストが報告されます。  
  
## 出力  
 MDA では、アセンブリが `LoadFrom` コンテキストに読み込まれたことが報告されます。  アセンブリの簡易名およびパスが指定されます。  また、`LoadFrom` コンテキストの使用を避けるための代替方法も提案されます。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 この MDA をアクティブ化する場合のコード例を次に示します。  
  
```  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## 参照  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
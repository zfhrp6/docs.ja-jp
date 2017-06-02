---
title: "方法 : アプリケーション ドメインにアセンブリを読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション ドメイン, 読み込み (アセンブリを)"
  - "読み込み (アセンブリを)"
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : アプリケーション ドメインにアセンブリを読み込む
アプリケーション ドメインにアセンブリを読み込むには、いくつかの方法があります。  推奨されているのは、[System.Reflection.Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx) クラスの `static` \(Visual Basic では `Shared`\) <xref:System.Reflection.Assembly.Load%2A> メソッドを使用する方法です。  それ以外には、以下の方法でアセンブリを読み込むことができます。  
  
-   [Assembly](https://msdn.microsoft.com/en-us/library/system.reflection.aspx) クラスの <xref:System.Reflection.Assembly.LoadFrom%2A> メソッドは、ファイルの場所が指定されたアセンブリを読み込みます。  このメソッドでアセンブリを読み込む場合は、別の読み込みコンテキストが使用されます。  
  
-   <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> メソッドと <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> メソッドは、リフレクション専用コンテキストにアセンブリを読み込みます。  このコンテキストに読み込まれたアセンブリはチェックできますが、実行することはできません。この結果、他のプラットフォームを対象とするアセンブリをチェックできます。  「[方法 : リフレクションのみのコンテキストにアセンブリを読み込む](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。  
  
> [!NOTE]
>  リフレクション専用コンテキストは、.NET Framework Version 2.0 で新たに追加されました。  
  
-   <xref:System.AppDomain> クラスの <xref:System.AppDomain.CreateInstance%2A> や <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> などのメソッドは、アプリケーション ドメインにアセンブリを読み込むことができます。  
  
-   <xref:System.Type> クラスの <xref:System.Type.GetType%2A> メソッドは、アセンブリを読み込むことができます。  
  
-   <xref:System.AppDomain?displayProperty=fullName> クラスの <xref:System.AppDomain.Load%2A> メソッドは、アセンブリを読み込むことができますが、主に COM の相互運用性のために使用されます。  このメソッドの呼び出し元であるアプリケーション ドメイン以外のアプリケーション ドメインにアセンブリを読み込む場合は、このメソッドを使用しないでください。  
  
> [!NOTE]
>  .NET Framework Version 2.0 以降では、現在読み込まれているランタイムよりもバージョン番号が新しい .NET Framework のバージョンでコンパイルされたアセンブリを、ランタイムが読み込まないようになりました。  これに該当するのは、バージョン番号のメジャー部分とマイナー部分を組み合わせた番号です。  
  
 読み込まれたアセンブリの Just\-In\-Time \(JIT\) コンパイル コードがアプリケーション ドメイン間で共有される方法を指定できます。  詳細については、「[Application Domains and Assemblies](http://msdn.microsoft.com/ja-jp/433b04ae-4ba8-4849-9dbd-79194f240346)」を参照してください。  
  
## 使用例  
 次に示すコードは、"example.exe" または "example.dll" という名前のアセンブリを現在のアプリケーション ドメインに読み込み、アセンブリから `Example` という型を取得し、さらにその型の `MethodA` というパラメーターを持たないメソッドを取得して、そのメソッドを実行します。  読み込まれたアセンブリから情報を取得する方法の詳細については、「[型の動的な読み込みおよび使用](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)」を参照してください。  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## 参照  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 [Hosting Overview](http://msdn.microsoft.com/ja-jp/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/ja-jp/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)   
 [方法 : リフレクションのみのコンテキストにアセンブリを読み込む](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)   
 [Application Domains and Assemblies](http://msdn.microsoft.com/ja-jp/433b04ae-4ba8-4849-9dbd-79194f240346)
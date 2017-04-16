---
title: "bindingFailure MDA | Microsoft Docs"
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
  - "binding failure"
  - "binding, failures"
  - "MDAs (managed debugging assistants), binding failures"
  - "assemblies [.NET Framework], binding failures"
  - "managed debugging assistants (MDAs), binding failures"
  - "BindingFailure MDA"
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# bindingFailure MDA
`bindingFailure` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、アセンブリの読み込みに失敗したときにアクティブになります。  
  
## 症状  
 コードは、静的参照またはいずれかのローダー メソッド \(<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> または <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>\) を使用して、アセンブリを読み込みしようとしました。  アセンブリは読み込まれず、<xref:System.IO.FileNotFoundException> 例外または <xref:System.IO.FileLoadException> 例外がスローされました。  
  
## 原因  
 バインディング エラーは、ランタイムがアセンブリを読み込むことができない場合に発生します。  バインディング エラーは、次のいずれかの状況の結果として発生することもあります。  
  
-   共通言語ランタイム \(CLR\) は、要求されたアセンブリを見つけることができませんでした。  この理由は数多くあります。たとえば、アセンブリがインストールされていない、アプリケーションがアセンブリを見つけるように正しく設定されていない、などです。  
  
-   一般的な問題のシナリオによって型が別のアプリケーション ドメインに渡されているが、このアプリケーション ドメインでは、CLR が読み込むアセンブリは、別のアプリケーション ドメインでその型を含んでいる必要があります。  別のアプリケーション ドメインが元のアプリケーション ドメインとは異なるように構成されていると、ランタイムがアセンブリを読み込むことができないことがあります。  たとえば、2 つのアプリケーション ドメインで、<xref:System.AppDomain.BaseDirectory%2A> プロパティ値が異なる可能性があります。  
  
-   要求されたアセンブリは、破損しているか、アセンブリではありません。  
  
-   アセンブリを読み込もうとしているコードには、アセンブリを読み込むための適切なコード アクセス セキュリティ許可が設定されていません。  
  
-   ユーザー資格情報には、ファイルを読み込むために必要なアクセス許可が設定されていません。  
  
## 解決策  
 最初の手順は、要求されたアセンブリに CLLR がバインドできなかった原因を決定することです。  たとえば「原因」セクションに一覧表示されたシナリオのように、ランタイムが要求されたアセンブリを見つけられなかったり読み込みできなかったりする理由は、数多く存在します。  バインディング エラーの原因を除去するには、次のアクションをお勧めします。  
  
-   `bindingFailure` MDA から提供されるデータを使用して、原因を特定します。  
  
    -   アセンブリ バインダーによって生成されるエラー ログを読み取るために、[Fuslogvw.exe \(アセンブリ バインディング ログ ビューアー\)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) を実行します。  
  
    -   アセンブリが要求された位置にあるかどうかを確認します。  <xref:System.Reflection.Assembly.LoadFrom%2A> メソッドおよび <xref:System.Reflection.Assembly.LoadFile%2A> メソッドの場合は、要求された場所を簡単に確認できます。  <xref:System.Reflection.Assembly.Load%2A> メソッドの場合は、アセンブリ ID を使用してバインドするため、アプリケーション ドメインの <xref:System.AppDomain.BaseDirectory%2A> プロパティ プローブ パスおよびグローバル アセンブリ キャッシュで、アセンブリ ID と一致するアセンブリを検索する必要があります。  
  
-   前の手順で確認した情報を基に、原因を解決します。  使用できる解決策は、次のとおりです。  
  
    -   要求されたアセンブリをグローバル アセンブリ キャッシュにインストールし、  ID でアセンブリを読み込むために <xref:System.Reflection.Assembly.Load%2A> メソッドを呼び出します。  
  
    -   要求されたアセンブリをアプリケーション ディレクトリにコピーし、ID でアセンブリを読み込むために <xref:System.Reflection.Assembly.Load%2A> メソッドを呼び出します。  
  
    -   <xref:System.AppDomain.BaseDirectory%2A> プロパティの変更かプローブ パスの追加により、バインディング エラーが発生するアプリケーション ドメインがアセンブリ パスを含むように再構成します。  
  
    -   ログオンしているユーザーがファイルを読み込むことができるように、ファイルのアクセス制御リストを変更します。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  バインディング エラーに関するデータを報告するだけです。  
  
## 出力  
 MDA は、読み込みに失敗したアセンブリを報告します。これには、要求されたパスや表示名、バインディング コンテキスト、読み込みが要求されたアプリケーション ドメイン、エラーの理由などが含まれます。  
  
 表示名や要求されたパスは、そのデータが CLR で利用できない場合は空白である場合があります。  失敗した呼び出しが <xref:System.Reflection.Assembly.Load%2A> メソッドに対する呼び出しであった場合、ランタイムは、アセンブリの表示名を決定できなかったことが考えられます。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 この MDA をアクティブ化する場合のコード例を次に示します。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## 参照  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
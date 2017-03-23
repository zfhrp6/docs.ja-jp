---
title: "方法: レジストリにキーを作成する (Visual C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "キー, 作成 (レジストリに)"
  - "レジストリ キー, 作成 [C#]"
  - "レジストリ, 追加 (キーと値を) [C#]"
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 方法: レジストリにキーを作成する (Visual C#)
現在のユーザーのレジストリに存在する "Names" というキーの下に "Name" と "Isabella" という値のペアを追加する例を次に示します。  
  
## 使用例  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## コードのコンパイル  
  
-   コードをコピーし、コンソール アプリケーションの `Main` メソッドに貼り付けます。  
  
-   `Names` パラメーターをレジストリの HKEY\_CURRENT\_USER ノードの直下にあるキーの名前に置き換えます。  
  
-   `Nam`e パラメーターを Names ノードの直下にある値の名前に置き換えます。  
  
## 信頼性の高いプログラミング  
 レジストリの構造を調べて、キーの適切な場所を見つけることができます。  たとえば、現在のユーザーの Software キーを開き、会社名のキーを作成できます。  その後で、会社名のキーにレジストリ値を追加します。  
  
 次の条件では例外が発生する可能性があります。  
  
-   キーの名前が null である場合。  
  
-   レジストリ キーを作成するためのアクセス許可がユーザーにない場合。  
  
-   キー名が 255 文字の制限を超えている場合。  
  
-   キーが閉じている場合。  
  
-   レジストリ キーが読み取り専用の場合。  
  
## .NET Framework セキュリティ  
 ローカル コンピューター \(`Microsoft.Win32.Registry.LocalMachine`\) よりもユーザー フォルダー \(`Microsoft.Win32.Registry.CurrentUser`\) にデータを書き込む方が安全です。  
  
 レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。  悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。  レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。  これを回避するために、`Overload:Microsoft.Win32.RegistryKey.GetValue` メソッドを使用します。  このメソッドは、キーがまだ存在しない場合、null を返します。  
  
 レジストリ キーがアクセス制御リスト \(ACL: Access Control List\) によって保護されていても、パスワードなど他人に知られたくないデータをプレーン テキストでレジストリに格納するのは危険です。  
  
## 参照  
 <xref:System.IO?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [Read, write and delete from the registry with C\# \(C\# によるレジストリからの読み取り、書き込み、削除\)](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
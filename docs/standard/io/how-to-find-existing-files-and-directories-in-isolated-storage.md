---
title: "方法 : 分離ストレージ内でファイルおよびディレクトリを検索する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ストア、検索 (ファイルとディレクトリを)"
  - "検索 (分離ストレージ ファイル内のファイルを)"
  - "ディレクトリ [.NET Framework]、分離ストレージ"
  - "分離ストレージ、検索 (ファイルとディレクトリを)"
  - "データ ストレージ (分離ストレージを使用した)、検索 (ファイルとディレクトリを)"
  - "ファイル [.NET Framework]、分離ストレージ"
  - "データ ストア、検索 (ファイルとディレクトリを)"
  - "検索 (分離ストレージ ファイル内のディレクトリを)"
  - "格納 (分離ストレージを使用したデータの)、検索 (ファイルとディレクトリを)"
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 分離ストレージ内でファイルおよびディレクトリを検索する
分離ストレージのディレクトリを検索するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=fullName> のメソッドを使用します。  このメソッドは検索パターンを表す文字列を取得します。  検索パターンで単一文字を表すワイルドカード文字 \(複数の文字をアスタリスク \(\*\) ワイルドカード文字を両方使用してワイルドカード文字は名前の最後の部分で使用する必要があります。  たとえば、`directory1/*ect*` は有効な検索文字列ですが、`*ect*/directory2` は無効です。  
  
 ファイルを検索するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=fullName> のメソッドを使用します。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> に適用される検索文字列がワイルドカード文字の制限は <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>に適用されます。  
  
 これらのメソッドのいずれも再帰的ではありません; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスには、ストア内のすべてのディレクトリまたはファイルを指定するためのメソッドは用意されていません。  ただし、再帰的なメソッドは次のコード例に示します。  
  
## 例  
 分離ストア内にファイルおよびディレクトリを作成する方法を次のコード例で示します。  最初に、ユーザーの分離されたストア、ドメインおよびアセンブリに `isoStore` の変数が取得され、表示されます。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> のメソッドを使用して複数の異なるディレクトリを設定するために使用されます <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> のコンストラクターはこれらのディレクトリにあるファイルを作成します。  次に、`GetAllDirectories` メソッドの結果全体を検索します。  このメソッドは、現在のディレクトリ内のすべてのディレクトリ名は、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> を使用します。  これらの名前は配列に格納され、その `GetAllDirectories` は自分自身を呼び出し、見つかった各ディレクトリに渡します。  その結果、すべてのディレクトリ名は配列で返されます。  次に、`GetAllFiles` メソッドを呼び出します。  このすべてのディレクトリの名前を検索メソッドの呼び出し `GetAllDirectories`、そのファイルが <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> のメソッドを使用して各ディレクトリを確認します。  結果は、表示のために配列で返されます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)
---
title: "方法 : 分離ストレージでファイルおよびディレクトリを削除する | Microsoft Docs"
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
  - "データ ストレージ (分離ストレージを使用した)、削除 (ファイルとディレクトリを)"
  - "ディレクトリ [.NET Framework]、分離ストレージ"
  - "ファイル [.NET Framework]、分離ストレージ"
  - "分離ストレージ、削除 (ファイルとディレクトリを)"
  - "データ ストア、削除 (ファイルとディレクトリを)"
  - "ストア、作成 (ファイルとディレクトリを)"
  - "削除 (分離ストレージ ファイル内のファイルを)"
  - "格納 (分離ストレージを使用したデータの)、削除 (ファイルとディレクトリを)"
  - "削除 (分離ストレージ ファイル内のディレクトリを)"
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 分離ストレージでファイルおよびディレクトリを削除する
分離ストレージ ファイル内のディレクトリやファイルを削除できます。  ストア内では、ファイル名やディレクトリ名は、オペレーティング システムの依存で、仮想ファイル システムのルートに関連するように指定します。  そのため、Windows オペレーティング システムでは大文字と小文字が区別されません。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=fullName> クラスには、ディレクトリやファイルを削除するための 2 種類のメソッドを指定する: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> と <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>。  <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外は、存在しないファイルやディレクトリを削除しようとするとスローされます。  名前にワイルドカード文字を含める場合は、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> は <xref:System.IO.IsolatedStorage.IsolatedStorageException> の例外と <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> をスロー <xref:System.ArgumentException> の例外をスローします。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> のメソッドはディレクトリにファイルまたはサブディレクトリが含まれている場合は失敗します。  既存のファイルおよびディレクトリを取得するために <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> と <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> のメソッドを使用できます。  ストアの仮想ファイル システムの検索の詳細については、「[方法 : 分離ストレージ内でファイルおよびディレクトリを検索する](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)」を参照してください。  
  
## 例  
 ディレクトリとファイルをいくつか作成し、その後で削除するコード例を次に示します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=fullName>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)
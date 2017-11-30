---
title: "方法 : 分離ストレージでファイルおよびディレクトリを削除する"
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
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>方法 : 分離ストレージでファイルおよびディレクトリを削除する
ディレクトリと、分離ストレージ ファイル内のファイルを削除することができます。 ストア内でファイルとディレクトリの名前はオペレーティング システムに依存、仮想ファイル システムのルートに対して相対的に指定されました。 Windows オペレーティング システムで区別することはできません。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>クラスは、ディレクトリとファイルを削除するための 2 つのメソッドを提供します。:<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>と<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>です。 <xref:System.IO.IsolatedStorage.IsolatedStorageException>ファイルまたは存在しないディレクトリを削除しようとする場合に例外がスローされます。 名前にワイルドカード文字を含める場合は<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>をスロー、<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外、および<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>をスロー、<xref:System.ArgumentException>例外。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>メソッド ディレクトリには、任意のファイルまたはサブディレクトリが含まれている場合は失敗します。 使用することができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>と<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>を既存のファイルとディレクトリを取得するメソッド。 ストアの仮想ファイル システムを検索する方法に関する詳細については、次を参照してください。[する方法: 既存のファイルを検索し、分離ストレージ内のディレクトリ](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)です。  
  
## <a name="example"></a>例  
 次のコード例では、作成し、いくつかのディレクトリとファイルを削除します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)

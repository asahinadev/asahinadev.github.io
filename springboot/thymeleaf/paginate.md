# layout/paginate.html
```html
<html xmlns:th="http://www.thymeleaf.org" class="h-100">
<head>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
	<!-- pagger -->
	<div th:fragment="pagination(page, uri)" class="container">
		<ul class="pagination pagination-sm" th:with="
		  n=${T(Math).max(page.number-5, 1)},
		  c=${page.getNumber()+1},
		  m=${page.getTotalPages()},
		  t=${page.getTotalPages()},
		  hasPrev=${page.hasPrevious()},
		  hasNext=${page.hasNext()},
		  a='active',
		  d='disabled',
		  b=''">
            <li th:data-disabled="${hasPrev == false}" th:data-active="false    " class="page-item" th:with="p=1     "><a class="page-link" th:href="@{${uri}(page=${p})}" >|&lt;</a></li>
			<li th:data-disabled="${hasPrev == false}" th:data-active="false    " class="page-item" th:with="p=${c-1}"><a class="page-link" th:href="@{${uri}(page=${p})}" > &lt;</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+0}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >1</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+1}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >2</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+2}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >3</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+3}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >4</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+4}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >5</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+5}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >6</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+6}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >7</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+7}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >8</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+8}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >9</a></li>
            <li th:data-disabled="${p       >   m   }" th:data-active="${c == p}" class="page-item" th:with="p=${n+9}"><a class="page-link" th:href="@{${uri}(page=${p})}" th:text="${p}" >10</a></li>
            <li th:data-disabled="${hasNext == false}" th:data-active="false    " class="page-item" th:with="p=${c+1}"><a class="page-link" th:href="@{${uri}(page=${p})}" > &gt;</a></li>
            <li th:data-disabled="${hasNext == false}" th:data-active="false    " class="page-item" th:with="p=${m}  "><a class="page-link" th:href="@{${uri}(page=${p})}" > &gt;|</a></li>
		</ul>
	</div>
</body>
</html>
```


# usage.html
```html
		<div th:insert="layout/pagenate::pagination(${list}, '/usage')"></div>
```

# UsageController.java
```java
	@GetMapping
	public String index(
			@PageableDefault() Pageable page,
			Model model) {
		model.addAttribute("list", usages.findAll(page));
		return "usage";
	}
```
# UsagesRepository.java
```java
@Repository
public interface UsagesRepository extends JpaRepository<Usage, Long> {
}
```

## T-PLAN 1

Система задумывалась, прежде всего, **для автоматизации обработки данных для составления финансовых прогнозов и отчётов по деятельности проектов**.

_Эти задачи в компании выполняют <del>ПО</del> PMO_ 
<abbr title="Project Manager Officer, администратор проекта">PMO</abbr>.

В процессе стало очевидным, что для создания указанных выше документов PMO требуются следующие актуальные и точные данные:

1. о графике работы сотрудников;
2. о планируемых и фактических отсутствиях;
3. о ставках;
4. о % занятости в проектах и пр.

> Все указанные данные поступают из разных источников, начиная рядовыми сотрудниками и заканчивая программными менеджерами, менеджерами отделов.
_____________________________________________

Соответственно, для полноценного выполнения задач система должна осуществлять:

- сбор данных и агрегацию их в едином месте
- обработку данных
- перемещение данных во внешние системы.

### Ролевая модель системы


<table>
  <!-- Шапка таблицы: названия колонок -->
  <thead>
    <tr>
      <th>Roles No.</th>                 <!-- Колонка 1: название режима -->
      <th>Role (name in system)</th>     <!-- Колонка 2: подробности -->
	  <th>Description</th>     
	  <th>Permission level</th>     
    </tr>
  </thead>

  <!-- Тело таблицы: строки с данными -->
  <tbody>
    <!-- Строка 1 -->
    <tr>
      <td><strong>R01<strong></td>      
      <td>Structure PMО</td>
	  <td>Structure PMO has permissions to perform distinct actions within the company structure unit(s) PMO is assigned to. <br>
	  An employee shall be assigned as Structure PMO on Admin page. <br>
	  <em>More than 1 structure unit shall be possible at the same time.<em></td>
	  <td>
- PMO of program <br>
- PMO of department <br>
- PMO of solution <br>
- PMO of subdiv <br>
- PMO of company <br>
</td>
    </tr>
	
	 <!-- Строка 2 -->
    <tr>
      <td><strong>R02<strong></td>      
      <td>Structure manager</td>
	  <td>Structure manager has permissions to perform distinct actions within the company structure unit(s) Manager is assigned to. <br>
	  An employee shall be assigned as Structure Manager on Admin page. <br>
	  </td>
	  <td>
- Program Manager <br>
- Department Manager <br>
- Solution Manager <br>
- Subdivision Manager <br>
- Company Manager (General Director) <br>
</td>
    </tr>
	
		 <!-- Строка 3 -->
    <tr>
      <td><strong>R03<strong></td>      
      <td>Project PMO</td>
	  <td>Project PMO has permissions to perform distinct actions within the project(s) this PMO is assigned to. <br>
An employee shall be assigned as Project PMO on Project Profile page of corresponding project. <br>
More than 1 projects shall be possible at the same time.
	  </td>
	  <td></td>
    </tr>
	
			 <!-- Строка 3\\4 -->
    <tr>
      <td><strong>R04<strong></td>      
      <td>Project Manager</td>
	  <td>Project Manager has permissions to perform distinct actions within the project(s) this Manager is assigned to. <br>
An employee shall be assigned as Project Manager on Project Profile page of corresponding project. <br>
More than 1 projects shall be possible at the same time.
	  </td>
	  <td></td>
    </tr>

  </tbody>
</table>





# laravel-union-paginator

simple paginator class add ability to paginate laravel union queries.

# Instruction of use
you can use laravel facades to call Paginator class.

```php
$first = DB::table('users')
            ->whereNull('first_name');

$users = DB::table('users')
            ->whereNull('last_name')
            ->union($first);

$page = 1;

$paginator = Paginator::setQuery($users)->setCurrentPage($page)->setPerPage(15);

$usersList = $paginator->getData();
```

# Inside view
```php
<table class="table bordered-table">
            <tbody class="table-body">
            @forelse($usersList as $user)
                <tr>
                    <td>{!! $user->name !!}</td>
                </tr>
            @empty
                <tr>
                    <td><h5>No results found</h5></td>
                </tr>
            @endforelse
            </tbody>
            <tfoot>
            <tr>
                <td>{!!  $paginator->links() !!}</td>
            </tr>
            </tfoot>
        </table>
```

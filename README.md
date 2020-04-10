# api là người bồi bàn. tiếp nhận yêu cầu của khách hàng và trả lại DL cho ng dùng dạng JSON

## link thực hành API

[thực hành API 1](https://www.toptal.com/laravel/restful-laravel-api-tutorial)

[thực hành API 2](https://blog.pusher.com/build-rest-api-laravel-api-resources/)


Route::get('/hello-world',function(Request $request){
   return response()->json('Hello World! Welcome to the first restful api',200);
});

Route::get('/books',function(){
    return Book::all();
});

Route::get('/books/{id}',function($id){
    return Book::findOrFail($id);
});

Route::post('/books',function(Request $request){
    return Book::create($request->all());
});

Route::patch('/books/{id}',function(Request $request, $id){
    $books = Book::findOrFail($id);
    $books->update($request->all());

    return $books;
});

Route::delete('/books/{$id}',function($id){
    return Book::destroy($id);

    return 204;
});

# ferrumDF

A DataFrame Library written mainly to work with my ML library,
Also can be used as stand alone.


# Usage

```
cargo add ferrumDF
```
or 
```
// in cargo.toml
ferrumDF = "0.1.1"
```

Example usage:

```
use std::time;
use crate::data_frame::read_from::read_csv;

#[test]
fn opening_df() {
    

    let start_time = time::Instant::now();
    let mut data = read_csv(r#"D:\file_name_!.csv"#, true , false).unwrap();
    //data.print_headers();
    print!("{:?}", start_time.elapsed());

    data.describe();

    data.set_headers(vec!["1" , "2" , "3" , "4" , "5" , "6"]);

    data.null_stats();
    data.print_headers();
    print!("{:?}", start_time.elapsed());
}


#[test]
fn opening_df_3() {
    let start_time = time::Instant::now();
    let mut data = read_csv("C:/file_name_2.csv", true , false).unwrap();
    //data.print_headers();
    //data.head();
    data.describe();    
    //data.describe_the("salary_in_usd", true);
    //data.normalize();
    //data.describe_the("salary_in_usd", true);
    dbg!(data.get_shape());
    //data.head();
    data.remove_columns(&vec![0]);
    data.encode("experience_level");
    //data.encode("employment_type");
    data.encode("job_title");
    data.encode("salary_currency");
    //data.encode("employee_residence");
    data.encode("company_location");
    data.encode("company_size");

    data.normalize();

    data.describe();

    //let h = data.train_test_split(0.2, 10, true);
    
    println!("{:?}", start_time.elapsed());

}

```
The Library is written to work with data frames larger than 1GB. Chunk reading will be introduced in future versions.

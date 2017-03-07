# Jinja2 Docker image

Basic image to use jinja2 cli agent. See usage here: https://github.com/mattrobenolt/jinja2-cli

## Example usage with container

#### Read data from stdin

    touch test.j2
    echo 'person: {{ name }}, {{ gender }}' > test.j2
    echo '{"name": "John Snow", "gender": "male"}' | docker \
        run --rm -i -v${PWD}/test.j2:/templates/test.j2 \
        slayerbirden/j2 jinja2 /templates/test.j2 > test.out

#### Use data file
    
    touch test.j2
    touch test.yml
    echo 'person: {{ name }}, {{ gender }}' > test.j2
    echo "name: Jaime Lannister
    gender: male" > test.yml
    docker run --rm -i -v${PWD}/test.j2:/templates/test.j2 \
        -v${PWD}/test.yml:/data/test.yml slayerbirden/j2 \
         jinja2 /templates/test.j2 /data/test.yml > test.out

## jinja2-cli LICENSE

https://raw.githubusercontent.com/mattrobenolt/jinja2-cli/master/LICENSE

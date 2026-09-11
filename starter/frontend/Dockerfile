FROM public.ecr.aws/docker/library/node:18.14.2-alpine3.17

WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install packages
RUN npm ci

# Copy code
COPY . .

# Build the app with the verified backend LoadBalancer URL
ENV DISABLE_ESLINT_PLUGIN=true
ENV CI=false
ENV REACT_APP_MOVIE_API_URL=http://a7e47d9fffb9b419e89747937e0874c9-2017450343.us-east-1.elb.amazonaws.com
RUN npm run build

# Expose the port used by the React app
EXPOSE 3000

# Start the React app when the container starts
CMD ["npm", "run", "serve"]